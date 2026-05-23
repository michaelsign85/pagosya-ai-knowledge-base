---
title: Seguridad, APIs y credenciales
version: v3
audiencia: merchants
actualizado_en: 2026-05-23
---

# Seguridad, APIs y credenciales

Este documento explica cómo PagosYa protege los datos, credenciales bancarias y accesos del negocio. El objetivo es que el merchant entienda qué nivel de protección tiene su información y qué buenas prácticas aplicar.

---

## Sección 1 — Autenticación y sesiones

### Cómo funciona el inicio de sesión

PagosYa usa **Supabase Auth** como motor de autenticación. Todo acceso al sistema requiere un **token JWT** (JSON Web Token) firmado y con tiempo de expiración. El token se genera al iniciar sesión y se usa en cada petición al backend.

**Métodos de acceso disponibles:**

| Método | Descripción |
|--------|-------------|
| **Email + contraseña** | Forma principal de acceso para owners y empleados |
| **Magic Link** | Enlace de acceso único enviado al email (sin contraseña) |
| **Invitación de empleado** | El owner envía un enlace con token temporal al empleado |

**Flujo de sesión:**
1. El usuario ingresa sus credenciales.
2. Supabase verifica las credenciales y emite un JWT de acceso con tiempo de expiración.
3. El JWT se adjunta automáticamente a cada petición al backend.
4. Si el token expira, se renueva automáticamente sin interrumpir la sesión.
5. Al hacer clic en "Cerrar sesión", el token se invalida en servidor.

> El sistema nunca almacena contraseñas en texto plano. Supabase usa bcrypt para almacenar credenciales de forma segura.

---

## Sección 2 — Roles de usuario y permisos

Cada usuario tiene un **rol** que determina qué puede ver y hacer dentro del sistema. El rol se almacena en la tabla `profiles` y se verifica en cada operación sensible.

### Tabla de roles y capacidades

| Rol | Descripción | Capacidades principales |
|-----|-------------|-------------------------|
| **Owner** | Dueño del negocio | Acceso completo a su tienda: POS, inventario, reportes, configuración, empleados, integraciones bancarias |
| **Employee** | Empleado asignado a una tienda | Solo POS, turno propio, clientes. Sin acceso a reportes financieros ni configuración |
| **Admin** | Administrador de la plataforma | Acceso a panel global, puede eliminar usuarios y gestionar integraciones de todos los merchants |
| **Reseller** | Revendedor del servicio | Acceso a su panel de comisiones y clientes captados |
| **Partner** | Socio integrador | Acceso según contrato de integración |

### Cómo se verifica el rol en las operaciones sensibles

Cuando una **Edge Function** (función del servidor) recibe una solicitud que requiere permisos elevados, hace la siguiente verificación:

1. Extrae el token JWT del header `Authorization`.
2. Crea un cliente Supabase con ese token (sin privilegios de admin).
3. Consulta el perfil del usuario en la tabla `profiles`.
4. Verifica que el rol sea el permitido para esa operación.
5. Solo si la verificación pasa, ejecuta la acción.

**Ejemplo real — eliminar un usuario:**
```
1. Recibir solicitud → verificar header Authorization
2. Obtener usuario actual por JWT → verificar que existe
3. Leer profiles.role del usuario actual → verificar que sea "admin"
4. Solo si role === "admin" → ejecutar eliminación
5. Si el admin intenta eliminarse a sí mismo → rechazar con error 400
```

---

## Sección 3 — Aislamiento de datos por tienda (RLS)

### Qué es RLS

**Row Level Security (Seguridad a Nivel de Fila)** es una característica de PostgreSQL/Supabase que garantiza que cada usuario **solo puede ver y modificar sus propios datos**, sin importar cómo se haga la consulta.

Esto significa que si dos merchants comparten la misma base de datos, nunca podrán ver los datos del otro, porque las políticas RLS los filtran automáticamente.

### Tablas protegidas con RLS

Todas las tablas de negocio tienen RLS habilitado:

| Tabla | Qué protege |
|-------|-------------|
| `tiendas` | Solo el owner puede ver sus propias tiendas |
| `profiles` | Cada usuario solo puede ver su propio perfil |
| `bank_integrations` | Solo el dueño ve sus credenciales bancarias |
| `audit_logs` | Solo el usuario que generó el log puede verlo |
| `cash_registers` | Solo el merchant ve los registros de caja de sus tiendas |
| `subscriptions` | Solo el merchant ve su suscripción |
| `api_key_requests` | Solo el merchant ve sus solicitudes de API bancaria |
| `categories`, `products`, `sales`, etc. | Filtradas automáticamente por `user_id` o `tienda_id` |

> Incluso si un atacante obtuviera acceso a la base de datos con las credenciales anónimas del frontend, no podría leer datos de otros merchants. Las políticas RLS actúan como una segunda capa de seguridad por encima de los tokens.

---

## Sección 4 — Protección de credenciales bancarias

### Dónde se almacenan

Las credenciales bancarias (API keys, tokens, contraseñas de banco) **nunca se envían al frontend** ni se almacenan en el navegador. El flujo es:

```
Frontend → Edge Function (servidor seguro) → API del banco
```

Las credenciales se guardan como **variables de entorno cifradas** en Supabase y se leen exclusivamente desde las Edge Functions (código de servidor).

### Qué banco usa qué mecanismo de seguridad

| Banco / Integración | Mecanismo de seguridad |
|---------------------|------------------------|
| **BNB** | Token JWT de sesión — validado por longitud, caracteres y formato antes de usar |
| **BANECO** | AES-256 — la contraseña se cifra usando el endpoint de encriptación del banco antes de enviarse |
| **Red Enlace QR** | Token Bearer con tiempo de vida limitado |
| **Red Enlace 3DS (tarjeta)** | HMAC SHA-256 (HTTP Signature) con `apiKeyId` y `sharedSecret` — ningún dato de tarjeta toca los servidores de PagosYa |
| **Cybersource** | HTTP Signature con clave compartida — autenticación por firma criptográfica de cada solicitud |

### Tabla `bank_integrations`

La tabla donde se registra qué banco está activo para cada merchant:

| Campo | Descripción |
|-------|-------------|
| `user_id` | ID del merchant dueño de la integración |
| `bank` | Nombre del banco: `BNB`, `RED_ENLACE`, `BANECO` |
| `api_key` | Referencia o ID de la integración (no la clave completa) |
| `is_active` | Solo puede haber 1 integración QR activa a la vez |
| `test_ok` | Si las credenciales pasaron la prueba de conexión |
| `integration_type` | Tipo: `QR` o `CARD` |

> Cuando el merchant activa un banco QR, el anterior se desactiva automáticamente. El sistema garantiza que solo haya **1 banco QR activo** por merchant en todo momento.

---

## Sección 5 — CORS y control de acceso a las APIs

### Qué es CORS

**CORS** (Cross-Origin Resource Sharing) controla qué dominios tienen permiso de hacer solicitudes al backend de PagosYa. Es la primera línea de defensa contra solicitudes de dominios no autorizados.

### Orígenes permitidos

Solo los siguientes dominios pueden llamar a las Edge Functions:

```
https://www.pagosya.com.bo
https://pagosya.com.bo
https://app.pagosya.com.bo
https://pagosya.vercel.app
http://localhost:5173    (desarrollo local)
http://localhost:3000    (desarrollo local)
capacitor://localhost    (app móvil iOS)
http://localhost         (app móvil Android)
```

Cualquier solicitud de un dominio no incluido en esta lista recibe una respuesta vacía o de error. El servidor **nunca refleja el origen desconocido** — siempre cae al dominio oficial.

### Edge Functions (funciones del servidor)

Las Edge Functions de PagosYa corren en un entorno **aislado** de Deno (Supabase Edge Runtime) con las siguientes garantías:

- No tienen acceso al sistema de archivos
- Las variables de entorno son cifradas en reposo por Supabase
- Cada función se ejecuta con el mínimo privilegio necesario
- Las funciones que necesitan privilegios de admin usan el `SUPABASE_SERVICE_ROLE_KEY` solo dentro del servidor, nunca lo exponen

---

## Sección 6 — Auditoría y logs

### Tabla `audit_logs`

PagosYa registra operaciones críticas en una tabla de auditoría protegida por RLS:

| Campo | Descripción |
|-------|-------------|
| `user_id` | Usuario que realizó la acción |
| `action` | Acción realizada (ej: `DELETE`, `UPDATE`, `CREATE`) |
| `table_name` | Tabla afectada |
| `record_id` | ID del registro afectado |
| `details` | Datos adicionales en formato JSON |
| `created_at` | Fecha y hora exacta |

### Logs de operaciones bancarias

Cada intento de autenticación con bancos, generación de QR y confirmación de pago genera registros internos en las Edge Functions, trazables por el equipo de soporte de PagosYa.

### Registros de turnos y caja

Las aperturas y cierres de turno se guardan en `cash_registers` con:
- Coordenadas GPS del dispositivo al abrir y cerrar
- Verificación de geofencing (si el dispositivo estaba en la ubicación correcta)
- Si la apertura/cierre fue desde la app móvil o desde web

---

## Sección 7 — Seguridad en integraciones bancarias (proceso completo)

### Cómo configurar una integración de forma segura

#### BNB

1. Ir a **Configuración → Integraciones Bancarias → BNB**.
2. Ingresar el `accountId`, `authorizationId` y, si aplica, la `merchantId`.
3. Hacer clic en **"Probar conexión"** — el sistema envía una solicitud de autenticación de prueba al banco.
4. Si la prueba es exitosa (`test_ok = true`), la integración queda activa.
5. Las credenciales se guardan cifradas en el servidor. El frontend no recibe la clave.

#### Red Enlace

1. El merchant envía una solicitud de integración desde el panel.
2. El equipo de PagosYa gestiona el proceso de afiliación con Red Enlace.
3. El admin de PagosYa activa la integración en el sistema cuando Red Enlace aprueba.
4. El merchant no necesita manejar las credenciales directamente.

#### BANECO

1. El merchant proporciona usuario y contraseña de su cuenta BANECO.
2. Al configurar, la contraseña **se cifra con AES-256** antes de ser enviada al banco para generar el token de sesión.
3. Los tokens tienen tiempo de vida limitado y se renuevan automáticamente en cada transacción.

---

## Sección 8 — Buenas prácticas para el merchant

### Contraseña de acceso

- Usar una contraseña de al menos **12 caracteres** con mayúsculas, números y símbolos.
- No compartir la contraseña de la cuenta owner con empleados.
- Usar el sistema de **invitación de empleados** para darles acceso limitado.
- Si un empleado deja el negocio, desactivarlo desde el panel de empleados.

### Empleados y accesos

- Cada empleado tiene su **propio acceso individual** — nunca un acceso compartido.
- El empleado solo puede ver el POS y sus propios turnos. No puede ver reportes financieros ni integraciones bancarias.
- Si se sospecha que un acceso fue comprometido, desactivar al empleado desde el panel inmediatamente.

### Dispositivos

- No dejar sesiones abiertas en dispositivos compartidos.
- En caso de pérdida de un dispositivo, cambiar la contraseña de la cuenta.
- La app móvil usa el mecanismo de sesión JWT — al cambiar la contraseña, los tokens anteriores quedan invalidados.

### Credenciales bancarias

- Nunca compartir las credenciales del banco con terceros.
- Si se sospecha que las credenciales BNB fueron comprometidas, desactivar la integración en el panel y contactar a soporte.
- El equipo de PagosYa **nunca solicitará por chat o teléfono** las credenciales bancarias.

---

## Preguntas frecuentes

**¿PagosYa puede ver los datos bancarios del negocio?**

No. Las credenciales bancarias se almacenan cifradas como variables de entorno en los servidores de Supabase y solo son accesibles por el código de servidor (Edge Functions), no por el equipo de PagosYa en forma directa. Las operaciones de pago se realizan directamente con el banco, sin intermediación de fondos.

**¿Puede un empleado ver los reportes de ventas o el saldo?**

No. Los empleados tienen acceso restringido al POS y a su propio turno. No pueden ver reportes financieros, integraciones bancarias, suscripciones ni configuraciones del negocio. El control de acceso se aplica en la base de datos (RLS) y en el servidor.

**¿Qué pasa si un empleado es eliminado del sistema?**

Su sesión se invalida y ya no puede iniciar sesión. Sus datos de actividad (ventas, turnos) quedan registrados en el historial del negocio para auditoría, pero su acceso es revocado de inmediato.

**¿Qué pasa si olvido mi contraseña?**

Desde la pantalla de inicio de sesión, usar "Olvidé mi contraseña". El sistema envía un enlace de recuperación al email registrado. El enlace tiene tiempo de expiración y es de un solo uso.

**¿Los datos del negocio están mezclados con los de otros merchants?**

En la base de datos comparten la misma infraestructura pero las políticas RLS garantizan que cada merchant solo puede acceder a sus propios datos. Es el mismo modelo de aislamiento que usan servicios como Stripe, Shopify o Supabase.

**¿Cómo sé qué banco está activo para mis cobros por QR?**

Desde el panel ir a **Configuración → Integraciones Bancarias**. El banco con `is_active = true` es el que se usa para generar todos los QR de cobro. Solo puede haber uno activo a la vez.

**¿PagosYa tiene acceso a mi dinero o puede moverlo?**

No. PagosYa no intermedia fondos. El QR de cobro es generado directamente con el banco del merchant. El dinero va directo a la cuenta bancaria del negocio sin pasar por cuentas de PagosYa.
