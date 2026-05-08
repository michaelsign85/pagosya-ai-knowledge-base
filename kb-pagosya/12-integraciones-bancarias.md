---
title: Integraciones bancarias y validación de pagos
version: v2
audiencia: merchants
actualizado_en: 2026-05-08
---

PagosYa se conecta directamente con los bancos bolivianos para validar pagos por QR de manera automática y segura.

## Bancos disponibles

- **BNB (Banco Nacional de Bolivia)** — integración activa y disponible para todos los comercios.
- **Banco Económico (BANECO)** — integración activa con QR Simple para Comercios.

---

## BNB — Banco Nacional de Bolivia

**¿Cómo activar la integración BNB?**
1. Desde PagosYa, ir a Configuraciones → Integraciones → BNB.
2. Completar el formulario con los datos del comercio.
3. El equipo de PagosYa gestiona el proceso con el banco.
4. En aproximadamente 2 días hábiles se reciben las credenciales (API Key).
5. Ingresar las credenciales en la sección correspondiente dentro de PagosYa.

---

## Banco Económico (BANECO) — QR Simple para Comercios

**¿Cómo activar la integración BANECO?**

Desde PagosYa, ir a Configuraciones → Integraciones → Banco Económico y completar el formulario. Hay tres opciones según la situación del comercio:

### Opción 1 — Persona Natural (ya tiene cuenta en BANECO)
Completar el formulario con:
- Nombre completo y número de CI
- Domicilio legal, ciudad, departamento
- Número de cuenta BANECO y tipo (ahorro / corriente)
- WhatsApp y correo electrónico

### Opción 2 — Persona Jurídica (ya tiene cuenta en BANECO)
Completar el formulario con:
- Razón social y NIT
- Nombre y CI del representante legal
- Domicilio legal, ciudad, departamento
- Número de cuenta BANECO y tipo (ahorro / corriente)
- WhatsApp y correo electrónico

### Opción 3 — Sin cuenta en Banco Económico
Para comercios que aún no tienen cuenta en BANECO. Solo se necesitan datos básicos (nombre, contacto, ciudad). El banco se encarga de todo el proceso de apertura de cuenta y habilitación del QR.

**Contacto directo en Banco Económico:**
- Responsable: **María de los Ángeles Ballivián Ross**
- WhatsApp: **+591 75336513**
- Email: **mballivian@baneco.com.bo**

**¿Qué pasa después de enviar el formulario?**
- El equipo del Banco Económico recibe la solicitud automáticamente.
- En aproximadamente 2 días hábiles el banco entrega: **usuario**, **contraseña** y **clave AES**.
- El comercio ingresa esas credenciales en la sección "Credenciales API" dentro de PagosYa para activar la integración.

---

## Validación de pagos (todos los bancos)

- Cada vez que un cliente paga por QR, el banco notifica a PagosYa vía **webhook**.
- PagosYa verifica el evento y actualiza el estado del pago en el POS o dashboard en tiempo real.
- Si el pago no es confirmado por el banco, el sistema lo marca como rechazado automáticamente.

**Ventajas**
- Confirmación automática en segundos.
- Seguridad bancaria garantizada.
- Sin intervención manual del comercio.

---

## Red Enlace — QR Interoperable

Red Enlace permite recibir pagos QR de **cualquier banco de Bolivia** (interoperabilidad total). PagosYa actúa como proveedor tecnológico de validación; el contrato es firmado directamente entre el comercio y Red Enlace.

**¿Cómo activar la integración Red Enlace?**

1. Desde PagosYa, ir a Configuraciones → Integraciones → Red Enlace.
2. Completar el formulario digital con:
   - Datos del negocio
   - Información del representante legal
   - Dirección y datos de contacto
   - Tipo de actividad comercial
3. El formulario es enviado automáticamente al equipo de Red Enlace.
4. Un agente autorizado de Red Enlace contacta al comercio para explicar el servicio, aclarar dudas y coordinar una visita presencial o reunión en oficinas.
5. El comercio firma los documentos contractuales directamente con Red Enlace.
6. En algunos días la integración queda activa y el comercio puede recibir pagos QR interoperables con confirmación automática en PagosYa.

**Condiciones comerciales**
- El contrato de operación de pagos QR es firmado **directamente con Red Enlace**.
- PagosYa mantiene un acuerdo estratégico con Red Enlace que permite pagos QR **sin comisión** hasta un monto máximo definido por Red Enlace.

**Rol de PagosYa**
PagosYa opera únicamente como sistema tecnológico: valida pagos, confirma en tiempo real e integra con POS, checkout y tienda online. PagosYa **no custodia fondos**, **no procesa pagos** y **no administra cuentas bancarias**.

**Beneficios**
- Integración con cualquier banco de Bolivia
- Pagos QR interoperables
- Validación automática y segura
- Un solo sistema para ventas físicas, online y reportes
