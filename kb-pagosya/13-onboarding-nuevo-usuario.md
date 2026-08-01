---
title: Onboarding y primeros pasos
version: v3
audiencia: merchants
actualizado_en: 2026-05-23
---

# Onboarding y primeros pasos

Este documento guía a un nuevo merchant desde el registro inicial hasta tener el sistema listo para cobrar. Cubre el registro, el período de prueba, la configuración básica y el acceso de empleados.

---

## Sección 1 — Período de prueba gratuito

Al registrarse por primera vez, todos los nuevos comercios reciben **14 días de prueba gratuita**, disponible para todos los planes, incluido Checkout Web:

| Característica | Detalle |
|----------------|---------|
| **Duración** | 14 días desde el registro |
| **Costo** | Gratis — sin tarjeta de crédito, sin compromiso |
| **Acceso** | Completo a todas las funcionalidades del sistema |
| **Límite de ventas** | Bs. 15,000/mes durante el período de prueba |
| **Requiere** | Solo email y contraseña |

> El período de prueba solo puede usarse una vez por persona. Si ya fue usado, el sistema lo detecta y solicita elegir un plan directamente.

Al terminar el período de prueba, el negocio debe elegir un plan para seguir usando el sistema. Mientras tanto, tiene acceso completo para evaluar todas las funcionalidades.

---

## Sección 2 — Registro del propietario

### Cómo registrarse

1. Ir a `app.pagosya.com.bo` o descargar la app móvil.
2. En la pantalla principal, hacer clic en **"Crear cuenta"** o **"Registrarse"**.
3. Completar el formulario de registro.

### Campos del formulario de registro

| Campo | Obligatorio | Descripción |
|-------|-------------|-------------|
| **Nombre completo** | Sí | Mínimo 2 caracteres |
| **Email** | Sí | Será el usuario de acceso al sistema |
| **Contraseña** | Sí | Mínimo 6 caracteres |
| **Confirmar contraseña** | Sí | Debe coincidir con la contraseña |
| **Teléfono** | Sí | Número de contacto del negocio |
| **Ciudad** | Sí | Ciudad boliviana donde opera el negocio |
| **CI (Carnet de Identidad)** | Opcional | Número de identificación personal |
| **Complemento CI** | Opcional | Complemento del CI si aplica |
| **Fecha de nacimiento** | Opcional | El sistema requiere ser mayor de 18 años |
| **Código de revendedor** | Opcional | Si fue referido por un revendedor PagosYa |
| **Aceptar Términos** | Sí | Checkbox obligatorio |

> El sistema verifica en tiempo real si el CI o el teléfono ya están registrados. Si detecta duplicado, avisa antes de enviar.

### Validaciones automáticas

- Si el email ya existe: mensaje de error con botón para ir al inicio de sesión
- Si el CI ya está registrado: advertencia visible mientras escribe
- Si el teléfono ya está registrado: advertencia visible mientras escribe
- Si el usuario es menor de 18 años: no permite continuar

### Anti-fraude

El formulario incluye verificación **Cloudflare Turnstile** (captcha invisible) para prevenir registros automatizados.

### Después del registro

- Si viene de una oferta de plan con compra directa → redirige al **checkout del plan elegido**
- Si es registro normal de prueba → redirige al **Dashboard**
- El sistema crea automáticamente el perfil del propietario con rol `owner`
- Se envía una notificación de bienvenida: **"🎁 ¡14 días gratis para ti!"**

---

## Sección 3 — Primera configuración recomendada

Una vez en el Dashboard, se recomienda completar estos pasos antes de empezar a vender:

### Paso 1 — Configurar la tienda

1. Ir a **Configuración → Mi Tienda** (o a **Tiendas** en el menú lateral).
2. Completar el nombre del negocio, dirección y ciudad.
3. Subir el logo del negocio.
4. Guardar.

### Paso 2 — Agregar productos al inventario

1. Ir a **Productos / Inventario** en el menú lateral.
2. Crear al menos un producto con nombre, precio y categoría.
3. Opcionalmente: agregar foto, descripción, stock mínimo y variantes.

> Los productos creados aparecen automáticamente en el POS y en la tienda online.

### Paso 3 — Configurar la integración bancaria (para cobrar por QR)

1. Ir a **Configuración → Integraciones Bancarias**.
2. Elegir el banco: **BNB** (autogestión) o **Red Enlace** (solicitud al equipo PagosYa).
3. Para BNB: ingresar las credenciales de la cuenta y hacer clic en **"Probar conexión"**.
4. Una vez verificado, el sistema está listo para generar QR de cobro.

> Si no configura la integración bancaria, el POS puede usarse para registrar ventas en efectivo mientras se gestiona la integración.

### Paso 4 — Realizar una venta de prueba

1. Ir al **POS** desde el menú lateral (ícono de caja registradora).
2. Abrir el turno de caja.
3. Agregar un producto al carrito.
4. Procesar el pago (efectivo o QR según lo configurado).
5. Verificar que la venta aparece en el Dashboard y en Reportes.

### Paso 5 — Invitar empleados (opcional)

1. Ir a **Empleados** en el menú lateral.
2. Hacer clic en **"Invitar empleado"**.
3. Ingresar nombre, teléfono y email del empleado.
4. El sistema genera un **enlace de invitación** con token único.
5. Enviar el enlace al empleado por WhatsApp o email.

---

## Sección 4 — Registro del empleado (flujo de invitación)

Los empleados no se registran solos — solo pueden unirse al sistema mediante un enlace de invitación enviado por el owner.

### Cómo registrarse como empleado

1. Abrir el enlace de invitación recibido (empieza con `app.pagosya.com.bo/employee-register?token=...`).
2. El sistema muestra el nombre del empleado (precargado desde la invitación) y el email.
3. Completar:
   - **Nombre completo** (editable si necesita corrección)
   - **Contraseña** (mínimo 6 caracteres)
4. Hacer clic en **"Registrarse"**.
5. El sistema vincula automáticamente al empleado con la tienda del owner.
6. Redirige a la pantalla de inicio de sesión con mensaje de confirmación.

> Si el empleado ya tenía una cuenta con ese email, el sistema intenta hacer login automáticamente con la contraseña proporcionada. Si la contraseña no coincide, muestra un error indicando que debe usar el inicio de sesión normal.

### Qué accede el empleado

Después de registrarse e iniciar sesión, el empleado ve solo:
- **POS**: procesar ventas
- **Su turno de caja**: abrir y cerrar el turno propio
- **Clientes**: consultar y crear clientes (si tiene permiso)
- Sin acceso a: reportes financieros, configuración, integraciones bancarias, otros empleados

---

## Sección 5 — Inicio de sesión

### Métodos disponibles

| Método | Cómo funciona |
|--------|---------------|
| **Email + contraseña** | Ingresar email y contraseña en la pantalla de acceso |
| **Magic Link** | Ingresar el email → recibir un enlace de acceso único por correo → hacer clic en el enlace |

El Magic Link es útil si se olvidó la contraseña o si se prefiere no tener contraseña.

### Recuperar contraseña

1. En la pantalla de inicio, hacer clic en **"¿Olvidé mi contraseña?"**.
2. Ingresar el email registrado.
3. Recibir el enlace de recuperación en el correo (caduca en pocos minutos).
4. Hacer clic en el enlace y establecer una nueva contraseña.

### Redirección post-login según rol

| Rol | Destino tras iniciar sesión |
|-----|---------------------------|
| **Owner** | Dashboard del negocio |
| **Employee** | Dashboard (vista limitada) con el POS disponible |
| **Admin** | Panel de administración global |
| **Reseller** | Dashboard de revendedor |
| **Partner** | Dashboard de socio |

---

## Sección 6 — Dashboard principal

Al entrar al sistema, el Dashboard muestra:

- **Barra de uso del plan**: ventas del período vs. límite del plan (con alerta si se acerca al límite)
- **Tarjetas de métricas**: total ventas del período, transacciones hoy, empleados activos
- **Gráfico de ventas**: área chart con evolución de ventas en el rango seleccionado
- **Tabla de ventas recientes**: listado de las últimas transacciones con búsqueda y filtro de fechas
- **Estado de turno de caja**: botón para abrir o cerrar el turno actual
- **Notificaciones**: ícono de campana con alertas del sistema (bienvenida, límite próximo, pago recibido)
- **Chat de soporte**: botón de acceso rápido al soporte PagosYa

Cuando llega un pago QR confirmado, aparece un **popup de pago recibido** con el monto y el nombre del comprador en tiempo real.

---

## Preguntas frecuentes

**¿Necesito tarjeta de crédito para el período de prueba?**

No. El período de prueba de 14 días es completamente gratuito y no requiere datos de pago. Solo email y contraseña.

**¿Cuál es el límite de ventas durante la prueba?**

Bs. 15,000/mes. Al elegir un plan, el límite sube según el plan: EmprendeYa (Bs.40,000), ExpandeYa (Bs.80,000), ConquistaYa y otros (Bs.150,000).

**¿Puedo empezar a vender el mismo día del registro?**

Sí. Desde el primer inicio de sesión se puede agregar productos y procesar ventas. Para cobrar por QR, primero hay que configurar la integración bancaria (BNB o Red Enlace).

**¿Mis empleados pueden registrarse solos?**

No. Los empleados solo pueden acceder mediante un enlace de invitación generado por el owner desde el panel. Esto garantiza que nadie se agregue sin autorización.

**¿Qué pasa si el período de prueba vence antes de elegir un plan?**

El acceso al sistema se restringe hasta elegir y pagar un plan. Los datos (productos, clientes, ventas) se conservan y están disponibles cuando se activa el plan.

**¿Puedo cambiar de plan durante la prueba?**

Sí. En cualquier momento de la prueba se puede ir a **Suscripción** y elegir un plan pagando directamente por QR. Los créditos de prueba no se descuentan del plan nuevo.
