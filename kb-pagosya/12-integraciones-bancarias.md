---
title: Integraciones bancarias y validación de pagos
version: v2
audiencia: merchants
actualizado_en: 2026-01-28
---

PagosYa es una plataforma tecnológica que permite a los comercios **validar pagos por QR de forma automática y segura**, integrándose con bancos y redes de pago autorizadas en Bolivia.

PagosYa **no custodia fondos ni procesa pagos**. Su rol es exclusivamente la **validación, notificación y control operativo** de los pagos recibidos.

---

## Integraciones disponibles

### 🔹 Red Enlace (Pasarela interoperable)
Integración activa mediante alianza estratégica.

- Permite operar con **cualquier banco de Bolivia**
- La relación contractual del servicio de pagos QR es **directamente entre el comercio y Red Enlace**
- PagosYa actúa como **sistema de validación y visualización del pago**

### 🔹 BNB – Banco Nacional de Bolivia
Integración bancaria directa.

- Disponible para comercios que operan con cuentas BNB
- Validación directa vía APIs bancarias

---

## Flujo de integración con Red Enlace

1. El comercio selecciona **Integración con Red Enlace** desde el menú **Configuraciones** en PagosYa.
2. Completa un **formulario digital** con los datos del negocio.
3. La solicitud es enviada automáticamente a **Red Enlace**.
4. Un **agente autorizado de Red Enlace** se comunica con el comercio para:
   - Explicar el servicio
   - Coordinar reunión o visita
   - Gestionar la firma de documentos
5. El comercio **firma el contrato directamente con Red Enlace**.
6. Red Enlace habilita la integración.
7. PagosYa recibe las credenciales técnicas y activa la validación en el sistema.

---

## Flujo de integración bancaria directa (BNB)

1. El comercio completa un formulario desde PagosYa.
2. Se envía la solicitud directamente al banco (correo seguro o API).
3. El banco revisa y autoriza las credenciales.
4. El comercio firma el documento de habilitación en una agencia del **BNB**.
5. PagosYa cifra y almacena las claves API de forma segura.

---

## Validación de pagos QR

- Cada vez que un cliente realiza un pago por QR:
  - El banco o Red Enlace notifica el evento vía **API o webhook**.
- PagosYa:
  - Verifica la autenticidad del pago
  - Valida el monto y la referencia
  - Registra la transacción
  - Muestra el estado del pago en el **POS y dashboard**
- Si el pago:
  - No existe
  - Está duplicado
  - No es confirmado  
  → el sistema lo marca como **rechazado**.

---

## Seguridad y cumplimiento

- Comunicación cifrada mediante **HTTPS / TLS**
- Validación bancaria en tiempo real
- No se almacenan credenciales bancarias en texto plano
- Uso de infraestructura cloud segura
- Registros y trazabilidad de eventos

---

## Ventajas para el comercio

- Confirmación automática de pagos en segundos
- Reducción de fraudes por comprobantes falsos
- Integración con cualquier banco (vía Red Enlace)
- Un solo sistema para:
  - Punto de venta (POS)
  - Checkout bancario
  - Tienda online
  - Reportes y control operativo
- Sin intervención manual del comercio

---

**PagosYa**  
Plataforma tecnológica de validación de pagos QR para comercios en Bolivia.
