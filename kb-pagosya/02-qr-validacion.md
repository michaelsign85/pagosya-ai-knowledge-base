---
title: Validación automática de pagos QR
version: v3
audiencia: merchants
actualizado_en: 2026-05-22
---

# Validación automática de pagos QR

PagosYa confirma automáticamente los pagos por QR bancario en segundos, sin que el comercio tenga que revisar capturas de pantalla ni llamar al banco. El dinero va directamente a la cuenta del comercio; PagosYa solo actúa como sistema de validación y confirmación.

---

## Por qué importa la validación automática

Muchos comercios en Bolivia aceptan pagos QR, pero siguen confiando en comprobantes enviados por WhatsApp para confirmar si el dinero llegó. Eso genera riesgo de fraude con capturas falsas, tiempo perdido revisando el banco y errores de registro.

Con PagosYa, cada vez que un cliente paga por QR, el banco notifica directamente al sistema. La confirmación aparece en pantalla en segundos, sin intervención del comercio.

---

## Bancos integrados

PagosYa soporta tres integraciones bancarias para pagos QR. Solo un banco puede estar activo a la vez por comercio.

| Banco | Tipo de integración | Interoperabilidad |
|-------|---------------------|-------------------|
| **BNB** (Banco Nacional de Bolivia) | Credenciales propias del comercio | Solo clientes BNB |
| **Banco Económico (BANECO)** | Credenciales propias del comercio | Solo clientes BANECO |
| **Red Enlace** | Modelo agregador (PagosYa) | Cualquier banco de Bolivia |

> Para aprender cómo activar cada integración, ver la documentación **12-integraciones-bancarias.md**.

---

## Tipos de QR disponibles

### QR Dinámico (valor fijo, uso único)

Generado en el momento de la venta con un valor exacto y una expiración definida. Es el tipo más común y el más seguro.

- Se crea automáticamente cada vez que el comercio inicia un cobro desde el **POS**, **Venta Rápida**, **Tienda Online** o **Checkout Externo**.
- El cliente escanea, paga el monto exacto y no puede pagar otro valor.
- Una vez pagado o expirado, el QR queda inválido.
- Compatible con BNB, BANECO y Red Enlace.

### QR Fijo (imprimible, valor abierto)

Un código QR permanente que el comercio puede imprimir y colocar en su local o vitrina. El cliente lo escanea, ingresa el valor que quiere pagar y completa la transacción sin que el comercio tenga que hacer nada.

- No requiere que el comercio esté mirando la pantalla.
- El cliente abre una página pública de pago (`pagosya.com.bo/pagar/[tienda]`), ingresa el monto y paga.
- La confirmación llega igual al sistema, en tiempo real.
- Disponible principalmente con **Red Enlace** (interoperable con todos los bancos).
- Con BNB también se puede generar un QR reutilizable de valor abierto.

---

## Cómo usar el cobro por QR — paso a paso

### Cobro desde Venta Rápida

La forma más directa de cobrar un monto específico por QR.

1. Desde el menú principal, seleccionar **Venta Rápida**.
2. Ingresar el monto a cobrar.
3. Seleccionar el método de pago **QR**.
4. El sistema genera un QR con el valor exacto.
5. Mostrar la pantalla al cliente para que escanee.
6. El cliente paga desde su app bancaria.
7. El sistema recibe la confirmación del banco y muestra **"✅ Pago confirmado"** automáticamente.
8. La venta queda registrada.

> Si el cliente tarda o cierra la pantalla, el QR tiene un tiempo de expiración. Se puede generar uno nuevo si es necesario.

---

### Cobro desde el POS

El POS sigue el mismo flujo, pero la venta ya tiene productos y totales calculados.

1. Agregar los productos al carrito desde el **POS**.
2. Al finalizar la venta, seleccionar **QR** como método de pago.
3. El sistema genera el QR con el total exacto de la venta.
4. El cliente escanea y paga.
5. El POS muestra la confirmación y la venta queda cerrada automáticamente.

---

### Cobro con QR Fijo (impreso)

Ideal para negocios donde el cliente llega, escanea y paga sin que el cajero intervenga (kioscos, locales pequeños, tiendas de autoservicio).

1. Desde **Configuraciones → QR Fijo**, generar el código QR de la tienda.
2. Descargarlo e imprimirlo.
3. Colocarlo en mostrador, vitrina o cualquier punto visible.

Cuando el cliente escanea:
1. El cliente escanea el QR con cualquier cámara o app bancaria.
2. Se abre la página pública de pago de la tienda.
3. El cliente ingresa el monto y opcionalmente una referencia (número de pedido, nombre, etc.).
4. El sistema genera un QR dinámico con ese valor.
5. El cliente paga desde su app bancaria.
6. El sistema confirma y registra la venta automáticamente.

---

### Checkout Externo (sitio web propio)

Para negocios que tienen su propio sitio web y quieren integrar el cobro QR de PagosYa.

- PagosYa genera un enlace o botón de pago que redirige al cliente al flujo de checkout.
- El cliente paga por QR y la confirmación llega al sistema del comercio mediante webhook.
- Requiere el **Plan Checkout Web** o **ConquistaYa** o superior.

> Más detalles en la documentación **08-tienda-online.md** y las guías de integración.

---

## Qué pasa cuando el cliente paga

Sin importar qué banco use el comercio ni desde dónde se inició el cobro, el flujo interno de confirmación es siempre el mismo:

1. El cliente completa el pago desde su app bancaria.
2. El banco envía una notificación automática (webhook) a los servidores de PagosYa.
3. PagosYa verifica que el monto, la referencia y el estado coincidan.
4. Si todo es correcto:
   - El estado de la transacción cambia a **"completado"**.
   - Se registra la venta en el historial del comercio.
   - El POS o pantalla de cobro muestra el mensaje de **"✅ Pago confirmado"** en tiempo real.
5. El dinero ya está en la cuenta bancaria del comercio (el proceso bancario es independiente).

> PagosYa **no retiene fondos**. El dinero pasa directamente del banco del cliente al banco del comercio.

---

## Protección contra comprobantes falsos

PagosYa elimina el riesgo de comprobantes manipulados porque **la confirmación viene directamente del banco**, no del cliente. El comercio nunca necesita pedir ni revisar una captura de pantalla para saber si un pago QR llegó.

Si un cliente dice que pagó pero el sistema no confirma, significa que el banco no procesó el pago. El comercio puede mostrar la pantalla de "pendiente" como evidencia y pedir al cliente que revise su app bancaria.

---

## Límites de ventas por plan

Cada plan de PagosYa incluye un límite mensual de ventas en bolivianos. Este límite aplica a todas las ventas confirmadas por QR y otros métodos dentro del sistema.

| Plan | Límite mensual |
|------|---------------|
| EmprendeYa | Bs. 40.000 |
| ExpandeYa | Bs. 80.000 |
| ConquistaYa / Checkout Web | Bs. 150.000 |
| RestauranteYa | Bs. 150.000 |

Si el comercio se acerca al límite o lo supera, el sistema bloquea nuevos cobros hasta que:
- empiece el siguiente período de suscripción, o
- el comercio agregue **créditos adicionales** para ampliar su capacidad temporalmente.

> Los créditos se compran desde **Configuraciones → Créditos** y se aplican de forma inmediata.

---

## Preguntas frecuentes

**¿El cliente necesita tener cuenta en el mismo banco?**

Depende de la integración activa:
- Con **BNB**: el cliente necesita usar la app del BNB.
- Con **BANECO**: el cliente necesita usar la app del Banco Económico.
- Con **Red Enlace**: el cliente puede pagar desde la app de **cualquier banco de Bolivia** (interoperabilidad total).

**¿Qué pasa si el pago no llega?**

Si el cliente pagó pero el sistema no confirma después de unos minutos, puede deberse a una demora temporal del banco. El comercio puede consultar el estado de la transacción desde el historial de ventas. Si el problema persiste, el equipo de soporte de PagosYa puede revisar los registros.

**¿Se puede cobrar sin internet?**

No. La confirmación automática requiere conexión a internet para recibir la notificación del banco. Sin conexión, el QR puede generarse, pero la confirmación no llegará hasta que se restablezca la conexión.

**¿Cuánto tiempo tarda en confirmar?**

En condiciones normales, la confirmación aparece en pantalla entre **3 y 15 segundos** después de que el cliente completa el pago en su app bancaria.

**¿Se puede tener más de un banco activo?**

No. Solo un banco puede estar activo a la vez por tienda. Si el comercio quiere cambiar de banco, debe desactivar el actual y activar el nuevo desde Configuraciones → Integraciones.

**¿El QR Fijo expira?**

El código QR impreso no expira (está vinculado a la URL permanente de la tienda). Cada vez que un cliente lo escanea, se genera un QR dinámico nuevo para esa transacción específica, que sí tiene expiración.
