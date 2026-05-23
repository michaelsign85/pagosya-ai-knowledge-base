---
title: Terminal POS — Funcionalidades completas
version: v3
audiencia: merchants
actualizado_en: 2026-05-22
---

# Terminal POS — Sistema de punto de venta

El **POS (Punto de Venta)** de PagosYa es el corazón del sistema para ventas presenciales. Desde aquí el cajero registra ventas, cobra pagos (efectivo, QR bancario o tarjeta), aplica descuentos, asigna clientes, imprime recibos y controla el inventario en tiempo real.

> Para acceder al POS, primero es necesario tener una **Caja abierta**. Sino, el sistema redirige automáticamente a la pantalla de apertura de caja.

---

## 1. Abrir y cerrar caja

La caja es el turno de trabajo del cajero. Cada venta queda registrada bajo la caja activa.

### Cómo abrir la caja

1. Ir a **Caja** desde el menú lateral.
2. Si hay múltiples tiendas, seleccionar en cuál se abrirá la caja.
3. Ingresar el **monto de apertura** (dinero físico que hay en la caja al inicio del turno).
4. Confirmar la apertura.

Una vez abierta, el indicador en la barra superior cambia a **"Caja Abierta"** con el nombre de la tienda y el tiempo transcurrido.

### Durante el turno — movimientos de caja

Desde la pantalla de Caja se pueden registrar:
- **Suprimento**: agregar dinero a la caja (por ejemplo, fondo de cambio adicional).
- **Sangria**: retirar dinero de la caja (por ejemplo, pago a proveedor durante el turno).

Todos los movimientos quedan registrados con el monto, motivo y usuario.

### Cómo cerrar la caja

1. Ir a **Caja → Cerrar caja**.
2. Ingresar el **monto de cierre** (dinero físico que quedó en la caja).
3. El sistema muestra el resumen del turno: ventas totales, desglose por método de pago, suprimentos y sangrias.
4. Confirmar el cierre.

> El historial de cierres de caja es la base para los reportes de turno y control de empleados.

---

## 2. Interfaz del POS

La pantalla del POS tiene dos áreas principales:

### Catálogo de productos (lado izquierdo / superior en mobile)

- **Barra de búsqueda**: buscar producto por nombre.
- **Filtro SKU**: buscar directamente por código interno del producto.
- **Filtros por categoría**: pestañas rápidas (Todos, Perfumes, Bebidas, etc.) para filtrar productos sin escribir.
- **Grilla de productos**: muestra foto, nombre, precio y stock disponible. Se cargan de a 25 productos por página.

### Carrito de venta (lado derecho / modal en mobile)

- Lista de ítems agregados, con cantidad y subtotal por línea.
- Controles para aumentar/disminuir cantidad o eliminar ítems.
- Sección de cliente, descuentos y total.
- Botón de cobro.

---

## 3. Agregar productos al carrito

### Por clic / toque

Hacer clic (o tocar en mobile) sobre el producto en la grilla. Si el producto tiene variaciones, el sistema muestra un selector de variaciones antes de agregar.

### Por búsqueda de nombre

Escribir en la barra de búsqueda. Los resultados se filtran en tiempo real. Hacer clic para agregar.

### Por código de barras — scanner físico

Si el comercio tiene una **pistola lectora USB o Bluetooth** conectada al dispositivo:

1. El scanner se detecta automáticamente — no requiere configuración especial.
2. Apuntar el laser al código de barras del producto.
3. El sistema detecta el código y agrega el producto automáticamente al carrito.
4. Si el producto ya estaba en el carrito, incrementa la cantidad.
5. Si el código no existe en el catálogo, no realiza ninguna acción (sin bloquear el flujo).

> El scanner funciona en cualquier parte de la pantalla del POS — no es necesario tener el cursor en ningún campo específico.

### Por código de barras — cámara del dispositivo

En dispositivos móviles con app instalada, se puede usar la cámara como scanner. El ícono de cámara en la barra de búsqueda activa este modo.

### Ajuste de cantidad

Una vez en el carrito, hacer clic en `+` o `-` para ajustar la cantidad. También se puede escribir directamente el número. Si el producto controla inventario y la cantidad supera el stock disponible, el sistema muestra una advertencia.

---

## 4. Agregar cliente a la venta

Antes de cobrar, se puede asociar un cliente a la venta para:
- Que el cliente acumule o use **puntos de fidelidad** (si el programa está activo).
- Que aparezca el nombre del cliente en el recibo.
- Que la venta quede registrada en el historial del cliente.

### Cómo asignar un cliente

1. En el carrito, hacer clic en el campo **"Buscar cliente"**.
2. Escribir el nombre, teléfono o CI del cliente.
3. Seleccionar de los resultados sugeridos.
4. Si el cliente no existe, se puede crear desde la pantalla de **Clientes** (o durante el proceso si el plan lo permite).

Si el programa de fidelidad está activo para la tienda, al seleccionar el cliente se muestra la cantidad de puntos disponibles.

---

## 5. Aplicar descuentos

### Descuentos predefinidos

1. En el carrito, hacer clic en **"Descuento"**.
2. Seleccionar uno o varios descuentos de la lista (los creados desde **Productos → Descuentos**).
3. El sistema aplica los descuentos de forma apilada:
   - Los descuentos de **porcentaje** se aplican secuencialmente sobre el monto ya descontado.
   - Los descuentos de **monto fijo** se restan directamente.
   - Los descuentos de **monto variable** permiten ingresar el monto en ese momento.
4. El total se actualiza en tiempo real mostrando cada descuento aplicado.

Se pueden aplicar **múltiples descuentos en la misma venta**.

### Canjeo de puntos de fidelidad

Si el cliente tiene puntos acumulados y el programa de fidelidad está activo:

1. Hacer clic en el ícono de estrella (⭐) o en **"Canjear puntos"**.
2. El sistema muestra los puntos disponibles del cliente y el equivalente en Bs.
3. Seleccionar cuántos puntos canjear.
4. El descuento equivalente se aplica automáticamente al total.

---

## 6. Métodos de pago

Al hacer clic en **"Cobrar"**, el sistema muestra las opciones de pago:

### Efectivo

1. Seleccionar **Efectivo**.
2. Ingresar el monto recibido del cliente.
3. El sistema calcula el **vuelto** automáticamente.
4. Confirmar el pago.

El sistema registra la venta inmediatamente y descuenta el stock.

### QR Bancario (pago dinámico)

1. Seleccionar **Código QR**.
2. El sistema genera un **QR dinámico** en tiempo real por el monto exacto de la venta.
3. El cliente escanea el QR con la app de su banco.
4. El sistema detecta automáticamente el pago confirmado (via Supabase Realtime + webhook del banco).
5. La venta se cierra automáticamente al recibir la confirmación.

Los bancos disponibles son los que estén configurados en la tienda:
- **BNB** (Banco Nacional de Bolivia)
- **BANECO** (Banco de la Comunidad)
- **Red Enlace** (pasarela multi-banco)

> Ver **02-qr-validacion.md** para la configuración bancaria paso a paso.

### Otros métodos

Al seleccionar **Otros**, se despliegan opciones para pagos no presenciales o con referencia:

| Método | Referencia requerida |
|--------|---------------------|
| Tarjeta de Débito | Número de referencia / NSU |
| Tarjeta de Crédito | Número de autorización |
| Transferencia Bancaria | Número de comprobante |
| QR Code Bancario (manual) | ID de transacción |

El cajero ingresa la referencia y confirma. Queda registrado como venta con método de pago correspondiente.

### Pago mixto (múltiples métodos)

Cuando el cliente paga con más de un método en la misma venta:

1. Seleccionar **Pago Mixto** (accesible desde la opción "Otros").
2. Agregar cada método con su monto:
   - Efectivo, QR, Tarjeta Débito, Tarjeta Crédito, Transferencia.
3. El sistema muestra el monto restante en tiempo real.
4. Para pagos QR dentro del mixto, genera el QR dinámico por el monto parcial.
5. Cuando todos los pagos suman el total, confirmar la venta.

---

## 7. Recibo y factura

### Recibo (actual)

Tras confirmar el pago, el sistema muestra el **recibo de venta** con:
- Nombre de la tienda, dirección, teléfono y logo.
- Número de venta (correlativo).
- Fecha y hora.
- Lista de productos con cantidad y precio.
- Descuentos aplicados.
- Total.
- Método de pago (con vuelto si fue en efectivo).
- Nombre del cliente (si se asignó).
- Puntos ganados y puntos acumulados (si el programa de fidelidad está activo).
- Nombre del empleado que atendió.

### Imprimir el recibo

- **App nativa (Android/iOS)**: Si hay una **impresora térmica** Bluetooth configurada, el botón "Imprimir" envía el recibo directamente.
- **Web (PC/browser)**: El botón "Imprimir" abre el diálogo de impresión del navegador.

### Compartir o descargar el recibo

El botón **"Compartir"** convierte el recibo en imagen y permite:
- Enviarlo por WhatsApp, email u otras apps.
- Descargarlo como archivo PNG.

### Factura electrónica SIAT (próximamente)

> El sistema de **facturación SIAT** está desarrollado y en proceso de homologación por el SIN. Una vez habilitado, el cajero podrá elegir entre emitir **Recibo** o **Factura** al momento del cobro.

Para emitir factura, el sistema solicitará:
- **NIT** del comprador.
- **Razón Social** del comprador.
- Email (opcional, para envío digital).
- Complemento (opcional).

Para ventas sin NIT específico, se podrá usar el NIT genérico **0 / "S/N"**, que emite una factura de consumidor final.

---

## 8. Guardar pedido (ventas en espera)

Si el cliente no está listo para pagar pero ya se tomó el pedido, se puede guardar para continuar después:

1. En el carrito, hacer clic en el ícono **"Guardar"** (💾).
2. Asignar un **nombre al pedido** (por ejemplo: "Mesa 5", "Cliente Juan", "Pedido para llevar").
3. Agregar **notas** opcionales.
4. Confirmar.

El carrito se limpia y queda disponible para una nueva venta.

### Recuperar un pedido guardado

1. Hacer clic en el ícono de **órdenes abiertas** (lista con reloj).
2. Se muestran todos los pedidos guardados del turno actual.
3. Seleccionar el pedido para cargarlo al carrito y continuar.

> En **Modo Restaurante**, el pedido guardado también puede enviarse a la estación de producción (cocina/barra) para preparación.

---

## 9. Modo Restaurante en el POS

Para comercios con el Modo Restaurante activo:

### Nota de cocina por ítem

Al agregar un producto al carrito, se puede tocar el ítem y agregar una **nota de cocina** (por ejemplo: "sin cebolla", "término 3/4", "extra salsa").

### Enviar a estación de producción

Antes de cobrar, se puede enviar los ítems a la **cocina** o **barra** para que empiecen la preparación:

1. Hacer clic en **"Enviar a producción"**.
2. Seleccionar la estación (cocina, barra, parrilla, etc.).
3. Se imprime o muestra el ticket de producción en la estación correspondiente.

Cuando el pedido se finaliza y se cobra, los **insumos de las recetas** se descuentan automáticamente del inventario.

---

## 10. Notas de la venta

Al guardar o finalizar una venta, se puede agregar una **nota general** a la orden. Esta nota queda registrada en el historial de ventas y es visible en los reportes y en el detalle de la transacción.

---

## Preguntas frecuentes

**¿Por qué no puedo entrar al POS?**

El POS requiere una caja abierta. Si el indicador dice "Sin caja abierta", ir a **Caja** desde el menú lateral y abrir la caja con el monto inicial.

**¿El scanner de código de barras funciona sin configuración?**

Sí. Cualquier lector USB o Bluetooth que funcione como teclado (HID) es compatible. Al conectarlo al dispositivo y escanear, el POS detecta el código automáticamente.

**¿Se puede cobrar sin QR dinámico si el internet falla?**

Sí. Si no hay internet, se puede cobrar con efectivo o con los métodos "Otros" (tarjeta/transferencia manual con número de referencia). El QR dinámico requiere conexión para generarse y validarse.

**¿La venta se guarda si cierro el navegador antes de cobrar?**

Las ventas no cobradas no se guardan automáticamente. Se recomienda usar **Guardar pedido** antes de cerrar, para no perder los ítems del carrito.

**¿Puedo ver cuánto se vendió en el turno?**

Sí. Desde **Caja**, el resumen del turno actual muestra el total de ventas, desglose por método de pago y movimientos de caja. El reporte completo está en **Reportes → Cierre de caja**.

**¿Se puede cambiar el precio de un producto en el POS?**

El precio del producto viene del catálogo. No se modifica directamente desde el POS. Para aplicar un precio especial, se recomienda usar un **descuento de monto variable** predefinido, o modificar el precio del producto desde **Productos** antes de la venta.

**¿La factura SIAT ya está disponible?**

El módulo de facturación SIAT está desarrollado en el sistema y aguarda la homologación oficial del SIN. Una vez habilitado, aparecerá la opción de elegir entre "Recibo" y "Factura" al momento del cobro.
