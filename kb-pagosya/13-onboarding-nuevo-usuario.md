---
title: Onboarding y primeros pasos
version: v3
audiencia: merchants
actualizado_en: 2026-05-23
---

# Onboarding y primeros pasos

Este documento guía a un nuevo merchant desde el registro inicial hasta tener el sistema listo para cobrar. Cubre el registro, la configuración básica y el acceso de empleados.

---

## Sección 1 — No hay período de prueba

PagosYa **no tiene período de prueba, trial ni plan de prueba**. No lo ofrezcas
ni lo menciones. Para usar el sistema hay que elegir y pagar un plan.

Si un lead pregunta si puede probar antes de pagar, tiene dos caminos (preguntá
cuál prefiere): ver los videos y el material en https://pagosya.com.bo/links, o
una demostración en vivo de 20 minutos con el equipo.

---

## Sección 2 — Registro del propietario

### Cómo registrarse

1. Ir a **www.pagosya.com.bo/planes** (o descargar la app móvil).
2. Elegir el plan y tocar su botón: se abre el formulario de registro con ese plan ya seleccionado.
3. Completar el formulario de registro.

> El único dominio de PagosYa es **www.pagosya.com.bo**. No existe `app.pagosya.com.bo`: nunca enviar ese enlace.
> Quien ya tiene cuenta inicia sesión en **www.pagosya.com.bo/auth**.

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

- Redirige al **checkout del plan elegido** para pagarlo por QR
- El sistema crea automáticamente el perfil del propietario con rol `owner`

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

1. Abrir el enlace de invitación recibido (empieza con `www.pagosya.com.bo/crear-cuenta?token=...`).
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

**¿Puedo probar el sistema gratis antes de pagar?**

No. No hay período de prueba. Para conocerlo antes de contratar: videos y material en https://pagosya.com.bo/links, o una demostración en vivo de 20 minutos.

**¿Puedo empezar a vender el mismo día del registro?**

Sí. Desde el primer inicio de sesión se puede agregar productos y procesar ventas. Para cobrar por QR, primero hay que configurar la integración bancaria (BNB o Red Enlace).

**¿Mis empleados pueden registrarse solos?**

No. Los empleados solo pueden acceder mediante un enlace de invitación generado por el owner desde el panel. Esto garantiza que nadie se agregue sin autorización.

**¿Necesito tarjeta de crédito?**

No. Los planes se pagan por QR bancario.
