---
title: Integraciones bancarias y validación de pagos
version: v1
audiencia: merchants
actualizado_en: 2025-10-25
---

PagosYa se conecta directamente con los bancos bolivianos para validar pagos por QR de manera automática y segura.

**Bancos actuales**
- **BNB (Banco Nacional de Bolivia)** — integración activa en fase de prueba.
- **BCP / IAP (Yape Bolivia)** — integración técnica en desarrollo y pruebas finales.

**Flujo de integración**
1. El comercio completa un formulario desde PagosYa.
2. Se envía solicitud directa al banco (vía correo seguro o API).
3. El banco revisa y autoriza las credenciales.
4. El usuario firma electrónicamente el documento de habilitación.
5. PagosYa cifra y almacena las claves API de forma segura.

**Validación de pago**
- Cada vez que un cliente paga por QR, el banco notifica vía **webhook o API**.
- PagosYa verifica el evento y muestra en el POS o dashboard el estado del pago.
- Si el pago es falso o no confirmado, el sistema lo marca como rechazado.

**Ventajas**
- Confirmación automática en segundos.
- Seguridad bancaria garantizada.
- Sin intervención manual del comercio.
