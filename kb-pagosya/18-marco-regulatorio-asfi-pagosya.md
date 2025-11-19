# Marco regulatorio – ASFI y modelo de negocio de PagosYa

## 1. Contexto general

PagosYa es una plataforma SaaS que ofrece herramientas tecnológicas para comercios en Bolivia, con foco en:

- Validación y confirmación automática de pagos por QR.
- Sistema POS e inventario.
- Reportes de ventas y control de empleados.
- Tienda online integrada con pagos por QR.

En ningún momento PagosYa recibe, custodia o redistribuye fondos de los usuarios finales. El dinero siempre se mueve directamente desde la cuenta del pagador hacia la cuenta del comercio en el banco correspondiente (por ejemplo, Banco BNB).

Por esta razón, PagosYa opera como **proveedor de servicios tecnológicos no financieros**, y no como entidad financiera ni como operador de un sistema de pagos.

---

## 2. Qué regula la ASFI en Bolivia

La Autoridad de Supervisión del Sistema Financiero (ASFI) regula y supervisa a las entidades que realizan actividades clasificadas como **servicios financieros** según la normativa boliviana (incluida la Ley de Servicios Financieros N° 393).

De forma simplificada, se considera actividad regulada cuando una empresa:

1. **Capta recursos del público**  
   - Por ejemplo: cuentas corrientes, cajas de ahorro, depósitos a plazo fijo, etc.

2. **Realiza intermediación financiera**  
   - Recibir dinero de unas personas o empresas para prestarlo o transferirlo a otras, asumiendo riesgo financiero.

3. **Opera como sistema de pago o procesador de pagos**  
   - Recibir fondos del pagador, procesarlos y luego liquidarlos o distribuirlos al beneficiario.
   - Manejar saldos de dinero dentro de la plataforma, “billeteras” internas, saldos a favor, etc.
   - Hacer “split” de pagos entre varios destinatarios.

4. **Presta servicios financieros complementarios**  
   - Por ejemplo: empresas de giros y remesas, casas de cambio, entidades emisoras de tarjetas de pago, etc.

En resumen:

> **Cuando una empresa toca el dinero (lo recibe, lo mantiene, lo reparte o lo liquida), la ASFI considera que está realizando una actividad financiera regulada y requiere autorización.**

Por el contrario:

> Si la empresa únicamente ofrece **tecnología**, **conectividad**, **validación de datos** y herramientas de gestión, sin recibir ni custodiar dinero, su actividad se considera **no financiera** y no requiere licencia de la ASFI.

---

## 3. Enfoque del modelo actual de PagosYa

### 3.1. Rol funcional de PagosYa

Hoy el modelo de PagosYa se basa en:

1. **Integración con APIs bancarias (por ejemplo, BNB)**  
   - PagosYa genera solicitudes de cobro y códigos QR utilizando las credenciales del comercio en el banco.
   - El QR pertenece a la cuenta del comercio, no a PagosYa.

2. **Validación y confirmación de pagos**  
   - PagosYa recibe notificaciones o consulta a la API del banco para verificar si un pago fue realizado.
   - Cambia el estado de la transacción dentro del sistema (pendiente, pagado, rechazado, etc.).

3. **Gestión operativa para el comercio**  
   - Registro de ventas.
   - Control de caja.
   - Reportes y estadísticas.
   - Control de empleados y tiendas.
   - Tienda online con cobro directo al banco del comercio vía QR.

En ninguna de estas etapas PagosYa:

- Recibe fondos en cuentas propias.
- Mantiene saldos de terceros.
- Redistribuye dinero entre usuarios.
- Se interpone como titular de los fondos.

### 3.2. Clasificación jurídica del modelo

Bajo esta lógica, PagosYa se ubica en la categoría de:

> **Proveedor de servicios tecnológicos de apoyo a comercios y bancos.**

Esto implica que:

- **No es un banco.**
- **No es una entidad financiera.**
- **No es un operador de sistema de pagos que custodia fondos.**
- **No realiza intermediación financiera.**

Por lo tanto, el modelo actual:

- **No requiere licencia de la ASFI como entidad financiera.**
- **No requiere autorización para captar depósitos ni ofrecer instrumentos financieros.**

Lo que sí se requiere es:

- Mantener **contratos y convenios claros** con los bancos (por ejemplo, BNB), especificando que:
  - El dinero siempre se acredita directamente a la cuenta del comercio.
  - PagosYa actúa únicamente como proveedor tecnológico.
- Cumplir buenas prácticas de:
  - Seguridad de la información.
  - Protección de datos personales.
  - Auditoría y registro de eventos (logs).

---

## 4. Límites claros del modelo (lo que PagosYa NO hace)

Para mantener la operación fuera del ámbito regulado financiero, PagosYa **NO debe**:

1. Recibir dinero de clientes finales en cuentas bancarias de PagosYa.
2. Mantener “saldos” de clientes dentro de la plataforma como si fuera una billetera electrónica.
3. Hacer distribución de fondos entre varios comercios (“split de pagos”) desde cuentas propias.
4. Ofrecer productos que se parezcan a depósitos, cuentas de ahorro, créditos o inversiones.
5. Publicitarse como entidad financiera, banco, billetera o pasarela que “recibe y retiene” el dinero.

Mientras el modelo se mantenga como:

> “**Sistema de validación y gestión de cobros por QR, donde el dinero va directo del pagador al comercio en el banco**, y PagosYa solo provee tecnología”

entonces **no se configura una actividad reservada a entidades reguladas por la ASFI.**

---

## 5. Mensaje resumido para usuarios y bancos

Cuando un usuario, banco o aliado pregunte por el tema regulatorio, PagosYa puede comunicar:

- PagosYa **no capta dinero del público**.
- PagosYa **no guarda ni administra fondos de terceros**.
- PagosYa **no realiza intermediación financiera**.
- Todo el dinero de los pagos **va directamente a la cuenta bancaria del comercio en el banco (por ejemplo BNB)**.
- PagosYa es una **plataforma tecnológica de validación y gestión**, no una entidad financiera.
- La relación regulatoria principal recae sobre:
  - El **banco** (por los servicios financieros que ofrece).
  - El **comercio** (por su actividad comercial).
- PagosYa mantiene **buenas prácticas de seguridad, registros y protección de datos**, y tiene documentación técnica y contractual disponible para los bancos y reguladores cuando se requiera.

---
