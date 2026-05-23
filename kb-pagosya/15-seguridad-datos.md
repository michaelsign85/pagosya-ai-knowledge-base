---
title: Seguridad, cifrado y privacidad de datos
version: v3
audiencia: merchants
actualizado_en: 2026-05-23
---

# Seguridad, cifrado y privacidad de datos

PagosYa fue construido con seguridad como principio base. Cada capa del sistema — desde la autenticación hasta el almacenamiento de credenciales bancarias — implementa controles de seguridad concretos y verificables en el código.

---

## Sección 1 — Autenticación y sesiones

### Cómo funciona el inicio de sesión

- **Proveedor**: Supabase Auth (sobre PostgreSQL + JWT)
- **Token**: JWT firmado por Supabase. Cada petición al backend lleva el token en el header `Authorization: Bearer <token>`
- **Expiración**: Los tokens expiran automáticamente. La sesión se renueva silenciosamente en el frontend mientras el usuario esté activo
- **Magic Link**: Supabase Auth envía un enlace de un solo uso al email del usuario. El enlace expira en minutos y solo puede usarse una vez

### Protección de contraseñas

Las contraseñas de usuarios **nunca se almacenan en texto plano**. Supabase Auth las almacena usando **bcrypt** (algoritmo de hashing con sal aleatoria). PagosYa no tiene acceso a las contraseñas originales.

### Sesiones de empleados

Los empleados se incorporan mediante un **token de invitación de un solo uso**. El token se genera al crear la invitación y se invalida automáticamente al ser usado.

---

## Sección 2 — Control de acceso por roles (RBAC)

PagosYa implementa un sistema de roles para separar lo que cada tipo de usuario puede ver y hacer:

| Rol | Descripción | Acceso |
|---|---|---|
| `owner` | Propietario del negocio | Acceso completo a su negocio |
| `employee` | Empleado de la tienda | POS, ventas, inventario básico |
| `admin` | Administrador de PagosYa | Panel administrativo global |
| `reseller` | Revendedor autorizado | Dashboard de revendedor |
| `partner` | Socio estratégico | Dashboard de socio |

### Verificación en Edge Functions

En cada función del backend, el flujo de verificación es:

1. Extraer el JWT del header `Authorization`
2. Verificar la firma del token con `supabase.auth.getUser(token)`
3. Consultar `profiles.role` en la base de datos para obtener el rol real
4. Si el rol no es el requerido → responder con `403 Forbidden`

> Los roles se verifican **en el servidor**, no en el frontend. El frontend puede ocultar elementos de UI, pero el acceso real está controlado por el backend.

---

## Sección 3 — Aislamiento de datos (Row Level Security)

Todas las tablas críticas en la base de datos tienen **Row Level Security (RLS)** activado en PostgreSQL. Esto significa que aunque un usuario intente consultar datos de otro usuario, la base de datos rechaza la consulta a nivel de motor — antes de que llegue a la aplicación.

### Tablas con RLS activado

| Tabla | Protege |
|---|---|
| `profiles` | Perfil del usuario |
| `subscriptions` | Plan y suscripción |
| `tiendas` | Tiendas del negocio |
| `ventas` | Historial de ventas |
| `transactions` | Transacciones de pago |
| `bank_integrations` | Credenciales bancarias |
| `credits` | Créditos del sistema |
| `cash_registers` | Cajas registradoras |
| `invites` | Invitaciones de empleados |
| `audit_logs` | Registros de auditoría |
| `employee_attendance` | Asistencia de empleados |
| `push_tokens` | Tokens de notificaciones push |
| `reseller_commissions` | Comisiones de revendedores |
| `api_key_requests` | Solicitudes de API |
| `support_tickets` | Tickets de soporte |

> Ningún usuario puede leer ni modificar datos de otro usuario aunque tenga acceso a la base de datos.

---

## Sección 4 — Cifrado de credenciales bancarias

Las credenciales bancarias (API keys, tokens, contraseñas) **nunca se almacenan en texto plano**.

### Mecanismo de cifrado por banco

| Banco | Mecanismo |
|---|---|
| **BNB** | JWT propio del banco. PagosYa guarda el token cifrado usando AES-256-GCM. Variable de entorno: `CREDENTIALS_ENC_KEY` |
| **BANECO** | Credenciales cifradas con AES-256 (modo CBC) antes de ser almacenadas. Variables: `BANECO_PROD_AES_KEY`, `BANECO_TEST_AES_KEY` |
| **Red Enlace** | Credenciales de API. Las claves en la base de datos se almacenan cifradas con AES-GCM. HMAC SHA-256 para verificar integridad en callbacks (header `x-api-key`) |
| **Cybersource / 3DS** | HMAC SHA-256 para firmar requests. Variables: `CYBERSOURCE_SHARED_SECRET`, `CYBERSOURCE_API_KEY_ID` |

### Campos en la tabla `bank_integrations`

| Campo | Descripción |
|---|---|
| `api_key` | Clave original (se pone en NULL después del cifrado) |
| `api_key_encrypted` | Clave cifrada con AES-GCM (base64: IV + cipher + tag) |
| `api_key_masked` | Versión enmascarada para mostrar en UI (ej: `•••••abc`) |
| `key_fingerprint` | Hash de la clave para comparar sin descifrar |
| `is_active` | Si la integración está activa |
| `test_ok` | Si pasó la prueba de conexión |
| `last_tested_at` | Fecha de la última prueba exitosa |

> El campo `api_key` original se establece en `NULL` después del proceso de cifrado. La clave descifrada **nunca se almacena en texto plano** en la base de datos.

---

## Sección 5 — CORS y aislamiento de Edge Functions

Las Edge Functions de PagosYa solo aceptan peticiones de orígenes autorizados. La lista de orígenes permitidos es fija en el código:

| Origen permitido | Uso |
|---|---|
| `https://www.pagosya.com.bo` | Sitio web principal |
| `https://pagosya.com.bo` | Sitio web (sin www) |
| `https://app.pagosya.com.bo` | Aplicación web |
| `https://pagosya.vercel.app` | Deploy en Vercel |
| `http://localhost:5173` | Desarrollo local (Vite) |
| `http://localhost:3000` | Desarrollo local alternativo |
| `capacitor://localhost` | App móvil iOS/Android |
| `http://localhost` | Capacitor Android |

Si una petición llega desde un origen no autorizado, la función responde con el origen fallback (`https://www.pagosya.com.bo`) — **nunca reflejando el origen desconocido**, lo que previene ataques CORS reflection.

Las funciones nuevas usan `buildSecureCorsHeaders(request)` que valida el origen dinámicamente. Las funciones heredadas usan `corsHeaders` con `*` pero están siendo migradas progresivamente.

---

## Sección 6 — Auditoría y registros de actividad

Todas las acciones críticas quedan registradas en la tabla `audit_logs`:

| Campo | Descripción |
|---|---|
| `user_id` | Usuario que realizó la acción |
| `action` | Tipo de acción (ej: `payment_confirmed`, `ticket_created`) |
| `table_name` | Tabla afectada |
| `record_id` | ID del registro afectado |
| `details` | Payload completo en formato JSON |
| `created_at` | Timestamp UTC de la acción |

### Qué se audita

- Confirmación de pagos (BNB, Red Enlace, BANECO)
- Cambios de estado en transacciones
- Acciones administrativas críticas

> Los logs de auditoría tienen RLS activado. Solo el administrador del sistema puede consultarlos globalmente.

---

## Sección 7 — Seguridad en integraciones de pago

### Callbacks y webhooks bancarios

Los endpoints de callback de los bancos están protegidos por una clave secreta en el header HTTP:

- **Red Enlace**: valida el header `x-api-key` contra la variable de entorno `RED_ENLACE_QR_CALLBACK_KEY`. Si no coincide → `401 Unauthorized`
- **Idempotencia**: antes de procesar un pago confirmado, el sistema verifica si ya fue procesado (`status === 'completed'`). Si es así, responde `200` sin reprocesar — evitando doble cobro
- **3DS (Cybersource)**: los requests se firman con HMAC SHA-256 usando `sharedSecret`. El banco verifica la firma antes de procesar

### Turnstile (captcha anti-fraude)

El formulario de registro de nuevos usuarios incluye **Cloudflare Turnstile** para verificar que el registro proviene de un humano real. El token de Turnstile se valida en el servidor antes de crear la cuenta.

---

## Sección 8 — Privacidad y protección de datos

### Principios aplicados

- **Mínimo privilegio**: cada rol accede solo a los datos que necesita
- **Datos en tránsito**: todas las comunicaciones van sobre HTTPS/TLS
- **Datos en reposo**: credenciales bancarias cifradas con AES-256-GCM
- **Separación de entornos**: variables separadas para producción y testing (`BANECO_TEST_*` vs `BANECO_PROD_*`, `CYBERSOURCE_ENV`)

### Lo que PagosYa NO hace

- No almacena números de tarjeta completos (PCI-DSS)
- No retiene fondos de pagos — los pagos van directamente a la cuenta bancaria del merchant
- No comparte datos de merchants ni clientes con terceros sin autorización
- No guarda contraseñas en texto plano

### Infraestructura

- **Base de datos**: PostgreSQL gestionado por Supabase (región: América del Sur)
- **Funciones backend**: Deno Edge Functions en Supabase (aislamiento por función)
- **Frontend**: Vercel CDN con headers de seguridad
- **Mobile**: App Capacitor con comunicación HTTPS únicamente

---

## FAQ — Preguntas frecuentes

**¿PagosYa puede ver mis claves bancarias?**
No. Las claves bancarias se cifran con AES-256-GCM antes de almacenarse. La clave original se elimina. Solo la Edge Function correspondiente puede descifrarlas temporalmente en memoria para hacer la operación.

**¿Qué pasa si alguien accede a mi cuenta por error?**
Cada usuario solo puede ver sus propios datos gracias al RLS de PostgreSQL. Incluso si alguien obtuviera un token válido de otro usuario, no podría ver datos de tu negocio.

**¿Los empleados pueden ver los reportes financieros?**
No. El control de acceso por roles impide que los empleados accedan a reportes financieros, configuración de integraciones bancarias o gestión de suscripciones.

**¿Cómo se protegen los pagos QR de doble cobro?**
El sistema verifica idempotencia antes de procesar: si el pago ya fue confirmado previamente (`status = completed`), la respuesta es exitosa pero no se vuelve a procesar la transacción.

**¿Mis datos están en Bolivia?**
Supabase almacena los datos en servidores de AWS región São Paulo (América del Sur), que es la región más cercana disponible. PagosYa no tiene servidores propios — usa infraestructura de nube.
