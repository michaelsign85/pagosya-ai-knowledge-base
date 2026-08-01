---
title: Gestión de productos e inventario
version: v4
audiencia: merchants
actualizado_en: 2026-07-06
---

# Gestión de productos e inventario

PagosYa incluye un sistema completo de catálogo e inventario integrado al POS, tienda online y reportes. El stock se descuenta automáticamente en cada venta y se actualiza en tiempo real en todas las tiendas.

---

## Límites de productos por plan

| Plan | Productos en catálogo |
|------|-----------------------|
| EmprendeYa | Sin límite de catálogo |
| ExpandeYa | Hasta 2.000 productos |
| ConquistaYa | Hasta 5.000 productos |
| RestauranteYa | Hasta 800 productos (menú) |

Si el comercio alcanza el límite, puede adquirir créditos adicionales desde el dashboard para ampliar el catálogo.

---

## Cómo crear un producto

1. Ir a **Productos** desde el menú principal.
2. Hacer clic en **"Nuevo producto"**.
3. Completar los datos del producto:

### Datos básicos

- **Nombre** — nombre del producto tal como aparecerá en el POS y tienda online.
- **Descripción** — texto opcional con detalles del producto.
- **Precio de venta** — precio que el cliente pagará.
- **Costo** — precio de costo (opcional, pero necesario para ver el margen real).
- **SKU** — código interno. Se genera automáticamente (6 dígitos), pero puede editarse.
- **Código de barras** — compatible con lectores físicos USB/Bluetooth. Al conectar un lector y posicionar el cursor en el campo, el código se completa automáticamente al escanear.
- **Categoría** — se puede asignar una o varias categorías al producto.
- **Activo** — determina si el producto aparece disponible en el POS y tienda online.

### Imágenes y galería

- Imagen principal del producto.
- Galería adicional: hasta 4 imágenes extras y 1 video corto.
- Las imágenes se muestran en el POS (modo visual) y en la tienda online.

### Tiendas y stock

Al crear un producto, se puede asignar a una o varias tiendas simultáneamente. Cada tienda puede tener:
- **Stock inicial** propio.
- **Stock mínimo** para alertas de reposición.
- **Lotes de entrada** con costo individual (ver sección de lotes).

### Configuración SIAT (factura electrónica)

Para comercios con facturación SIAT activa, cada producto necesita 3 campos fiscales:
- Código de producto SIN
- Código de actividad económica
- Unidad de medida SIN

> El buscador de productos SIAT está integrado: al escribir el nombre del producto, el sistema sugiere las opciones del catálogo oficial del SIN.

**Importante — estos 3 campos son obligatorios cuando la tienda tiene SIAT activo.** El botón "Guardar"/"Actualizar" del producto queda deshabilitado hasta completarlos. Si un producto quedó sin estos datos (por ejemplo, creado antes de activar SIAT), el POS bloqueará la venta a crédito fiscal de ese producto hasta que se complete su ficha en Productos → editar → "Buscar Producto SIAT". Ver documento `31-facturacion-siat-electronica.md` para el flujo completo.

---

## Productos con variaciones

Un **producto variable** es un producto que existe en diferentes opciones, como talla, color, sabor o presentación. Cada variación tiene su propio stock e imagen, pero comparten el mismo nombre base, precio y datos generales.

**Ejemplos:** Remera (S/M/L/XL), Zapatilla (talla + color), Refresco (tamaño 500ml / 1L / 2L).

### Cómo crear un producto con variaciones

1. Al crear o editar un producto, activar la opción **"Este producto tiene variaciones"**.
2. Definir los atributos de variación (por ejemplo: "Talla" con opciones S, M, L, XL; o "Color" con opciones Rojo, Azul, Negro).
3. El sistema genera automáticamente todas las combinaciones posibles.
4. Para cada variación se puede definir:
   - Stock por tienda
   - Stock mínimo
   - Imagen específica de la variación
   - Lotes de entrada con costo
5. Guardar el producto.

En el POS, al seleccionar el producto, el sistema muestra las variaciones disponibles para que el cajero elija la correcta antes de agregar al carrito.

---

## Control de inventario por lotes (Costo Medio Ponderado)

El sistema permite registrar las **entradas de stock por lote**, indicando la cantidad y el costo unitario de cada compra. Esto permite conocer el costo real del inventario en todo momento.

### Por qué usar lotes

- Cada vez que el comercio recibe mercadería, puede registrar el costo exacto de esa compra.
- Si en distintas compras el precio del proveedor fue diferente, el sistema calcula automáticamente el **costo medio ponderado** considerando todos los lotes activos.
- Esto da un costo de producto más preciso, que se usa en los reportes de margen de ganancia.

### Cómo registrar un lote de entrada

Al crear o editar un producto, dentro de la sección de tiendas:

1. Seleccionar la tienda.
2. Hacer clic en **"+ Agregar lote"**.
3. Ingresar:
   - **Cantidad** de unidades recibidas.
   - **Costo unitario** de esta compra.
   - **Nota** opcional (número de factura del proveedor, fecha de vencimiento, etc.).
4. Se pueden agregar múltiples lotes.
5. El sistema calcula el costo promedio automáticamente a partir de todos los lotes.

### Cómo funciona el costo promedio

El costo almacenado en el producto es el costo medio ponderado de todos los lotes activos:

```
Costo promedio = Suma(cantidad × costo por lote) / Suma(cantidad total)
```

Este valor se actualiza cada vez que se agrega un nuevo lote o se modifica uno existente.

---

## Alertas de stock bajo

PagosYa avisa cuando los productos se están agotando, para que el comercio pueda reponerlos a tiempo.

### Cómo configurar el stock mínimo

Al crear o editar un producto, ingresar el valor de **Stock mínimo** en el campo correspondiente (por tienda). Cuando el stock disponible llegue a ese nivel o lo supere, el sistema activa la alerta.

### Dónde se ven las alertas

- En la pantalla de **Productos**, aparece un indicador con la cantidad de productos en alerta.
- Se puede filtrar la lista para ver solo los productos con **stock bajo** o **sin stock**.
- Las alertas se clasifican en:
  - **Crítico**: stock en cero (indicador rojo "SEM STOCK").
  - **Advertencia**: stock por debajo del mínimo configurado.

---

## Categorías de productos

Las categorías permiten organizar el catálogo y facilitar la búsqueda en el POS y en la tienda online. Las categorías son compartidas entre todas las tiendas del mismo comercio.

### Cómo crear una categoría

1. Desde la pantalla **Productos**, hacer clic en **"Categorías"** (botón en la esquina superior derecha).
2. Hacer clic en **"+ Nueva categoría"**.
3. Completar:
   - **Nombre** — por ejemplo: Perfumes, Bebidas, Snacks, Postres.
   - **Descripción** — opcional, para uso interno.
4. Guardar.

La categoría queda disponible de inmediato para asignarla a productos.

### Cómo editar o eliminar una categoría

- Hacer clic en el ícono de **edición** (lápiz) junto a la categoría para cambiar su nombre o descripción.
- Hacer clic en el ícono de **eliminar** (basura) para desactivarla. Los productos que tenían esa categoría no se pierden; solo dejan de estar agrupados bajo ella.

### Uso de las categorías

- **En el POS**: las categorías aparecen como filtros rápidos en la barra lateral, permitiendo al cajero encontrar productos más rápido sin necesidad de buscar por nombre.
- **En la tienda online**: las categorías organizan el menú de navegación del cliente.
- **En el listado de productos**: se puede filtrar por categoría para ver, editar o exportar un grupo de productos.
- **Un producto puede pertenecer a varias categorías** al mismo tiempo.

---

## Descuentos

Los descuentos permiten aplicar rebajas fácilmente desde el POS sin calcular manualmente. Se crean una sola vez y quedan disponibles para todos los empleados y tiendas del comercio.

### Tipos de descuento

| Tipo | Descripción | Ejemplo |
|------|-------------|---------|
| **Porcentaje** | Rebaja un % sobre el subtotal | 10%, 15%, 20% |
| **Monto fijo** | Descuenta un monto fijo en Bs. | Bs. 5, Bs. 20 |
| **Monto variable** | El cajero ingresa el monto en el momento | Descuento a criterio |

### Cómo crear un descuento

1. Desde **Productos**, hacer clic en **"Descuentos"** (botón en la esquina superior derecha).
2. Hacer clic en **"+ Nuevo descuento"**.
3. Completar:
   - **Nombre** — nombre descriptivo, por ejemplo: "Descuento cliente VIP", "Promo fin de semana", "Cortesía".
   - **Tipo** — seleccionar entre Porcentaje, Monto fijo o Monto variable.
   - **Valor** — ingresar el porcentaje o monto (no aplica para Monto variable, que se define al momento de vender).
4. Guardar.

El descuento queda disponible en el POS para todos los cajeros de todas las tiendas.

### Cómo aplicar un descuento en el POS

Durante una venta en el POS:
1. Agregar los productos al carrito.
2. Hacer clic en **"Descuento"** en el resumen de la venta.
3. Seleccionar el descuento predefinido de la lista, o ingresar el monto manualmente si es tipo variable.
4. El sistema recalcula el total automáticamente mostrando el descuento aplicado.

> El descuento se aplica sobre el **subtotal total del carrito**, no sobre productos individuales.

### Cómo editar o eliminar un descuento

- Hacer clic en el ícono de edición para cambiar el nombre, tipo o valor.
- Hacer clic en el ícono de eliminar para desactivarlo. Los descuentos eliminados no afectan el historial de ventas anteriores.

---

## Transferencia de stock entre tiendas

Cuando el comercio tiene múltiples sucursales, puede mover stock de una tienda a otra sin registrarlo como venta. Esto es útil para equilibrar el inventario entre puntos de venta.

### Cómo hacer una transferencia

1. Desde **Productos**, hacer clic en **"Transferir Stock"** (botón en la esquina superior derecha).
2. En la pestaña **"Nueva transferencia"**:
   - Seleccionar la **tienda de origen** (de donde sale el stock).
   - Seleccionar la **tienda de destino** (a donde llega el stock).
   - Buscar el **producto** a transferir (solo se muestran los productos con stock disponible en la tienda de origen).
   - Ingresar la **cantidad** a transferir.
   - Agregar una **nota** opcional (motivo, referencia interna, etc.).
3. Confirmar la transferencia.

> El sistema valida que la cantidad solicitada no supere el stock disponible en la tienda de origen. Si no hay suficiente stock, muestra un error antes de ejecutar la transferencia.

### Historial de transferencias

En la pestaña **"Historial"** se puede ver el registro de todas las transferencias realizadas, con:
- Tienda de origen y destino.
- Producto y cantidad transferida.
- Fecha y usuario que realizó la operación.
- **Estado** de la transferencia:
  - `Pendiente`: registrada pero no confirmada.
  - `Completada`: transferencia ejecutada con éxito.
  - `Cancelada`: transferencia anulada antes de completarse.

El historial puede filtrarse por tienda de origen, tienda de destino y estado.

---

## Importar y exportar productos (CSV)

### Importar desde CSV

Para cargar muchos productos de una vez:
1. Ir a **Productos → Importar**.
2. Descargar la plantilla CSV para ver el formato correcto.
3. Completar la plantilla con los productos.
4. Subir el archivo CSV.
5. El sistema procesa e importa los productos a la tienda seleccionada.

> Tip: la importación acepta tanto coma (`,`) como punto y coma (`;`) como separadores, para compatibilidad con Excel en configuraciones de idioma español.

### Exportar a CSV

Para descargar el catálogo completo:
1. Ir a **Productos → Exportar**.
2. El sistema descarga un archivo CSV con todos los productos, precios, stock y categorías.

---

## Inventario avanzado — Modo Restaurante

Los comercios con **Modo Restaurante** activo tienen acceso a un sistema de inventario adicional basado en **insumos** y **recetas**. Este módulo está diseñado para negocios de gastronomía donde los productos del menú se elaboran a partir de ingredientes con stock propio.

> El Modo Restaurante está disponible para el plan **RestauranteYa** y puede activarse como módulo adicional en otros planes.

---

### Insumos (ingredientes)

Un **insumo** es un ingrediente o materia prima que se usa para preparar los productos del menú. Tiene su propio stock, costo y unidad de medida.

**Ejemplos:** harina, leche, queso, pollo, aceite, papel para empaque.

#### Cómo registrar un insumo

1. Ir a **Productos → Insumos** (pestaña disponible cuando el Modo Restaurante está activo).
2. Hacer clic en **"Nuevo insumo"**.
3. Completar:
   - **Nombre** del insumo.
   - **Categoría** (opcional, para organizar: lácteos, carnes, secos, etc.).
   - **Unidad base**: `g` (gramos), `ml` (mililitros) o `unidad`.
   - **Stock mínimo** para alertas de reposición.
4. Guardar.

#### Registrar una entrada de insumo (compra)

Cada vez que el comercio recibe mercadería, se registra una entrada:

1. En la lista de insumos, seleccionar el insumo.
2. Hacer clic en **"Registrar entrada"**.
3. Completar:
   - **Cantidad comprada** (puede ingresarse en kg y el sistema convierte a gramos automáticamente, igual con litros → ml).
   - **Unidad de compra** (kg, g, l, ml, unidad).
   - **Costo total de la compra** en Bs.
   - **Motivo** o referencia opcional.
4. Guardar.

El sistema calcula automáticamente el **costo unitario base** (costo por gramo/ml/unidad) a partir del total pagado y la cantidad recibida.

#### Alertas de insumos bajos

Igual que los productos, cada insumo tiene un **stock mínimo**. Cuando el stock actual del insumo cae por debajo del mínimo:
- Aparece una alerta visual en la lista de insumos (los insumos con alerta se muestran primero).
- El sistema envía una notificación al propietario para avisar que el insumo necesita reposición.
- La notificación no se repite hasta que el stock sea repuesto por encima del mínimo.

---

### Recetas (Ficha técnica)

Una **receta** o ficha técnica es la lista de insumos que se consumen al preparar y vender un producto del menú. Al configurar una receta, el sistema descuenta automáticamente los insumos correspondientes cada vez que se vende ese producto.

**Ejemplo:** Hamburguesa clásica = 150g de pan + 200g de carne + 20g de queso + 10g de lechuga.

#### Cómo configurar la receta de un producto

1. Ir a **Productos** y editar el producto del menú.
2. Activar la sección **"Receta / Ficha técnica"**.
3. Agregar líneas de receta:
   - Seleccionar el **insumo**.
   - Ingresar la **cantidad que se usa** por unidad vendida.
4. El sistema muestra en tiempo real:
   - **Costo de producción**: suma del costo de todos los insumos según las cantidades de la receta.
   - **Ganancia bruta**: precio de venta menos costo de producción.
   - **Margen porcentual**: porcentaje de ganancia sobre el precio de venta.
5. Guardar.

#### Cómo funciona el descuento automático

Cada vez que un producto con receta se vende desde el POS:
1. El sistema identifica la receta del producto.
2. Descuenta la cantidad de cada insumo según la receta.
3. El stock de los insumos se actualiza automáticamente.
4. Si algún insumo queda por debajo del stock mínimo, se activa la alerta.

Todo queda registrado en el **historial de movimientos de insumos**, con referencia a la venta que generó el consumo.

#### Historial de movimientos de insumos

Cada insumo tiene un historial completo con los siguientes tipos de movimiento:
- **Entrada** (compra): cuando se registra una compra de insumo.
- **Salida** (venta): consumo automático generado por una venta con receta.
- **Ajuste manual**: corrección de inventario hecha por el usuario.
- **Desperdicio**: registro de pérdida o merma.

---

## Preguntas frecuentes

**¿El stock se descuenta automáticamente al vender?**

Sí. Cada vez que se confirma una venta desde el POS, la tienda online o el checkout, el stock de los productos vendidos se descuenta automáticamente. Para el Modo Restaurante, también se descuentan los insumos de las recetas configuradas.

**¿Qué pasa si intento vender un producto sin stock?**

El sistema muestra una advertencia. El cajero puede optar por continuar la venta o cancelarla. El propietario puede configurar si permite ventas con stock negativo.

**¿Puedo tener el mismo producto en varias tiendas?**

Sí. Al crear un producto, se selecciona en qué tiendas estará disponible. Cada tienda puede tener un stock diferente para el mismo producto. El SKU es el identificador que conecta el mismo producto entre tiendas.

**¿El costo promedio se recalcula solo?**

Sí. Cada vez que se agrega un nuevo lote de compra, el sistema recalcula automáticamente el costo medio ponderado del producto considerando todos los lotes activos.

**¿Puedo cambiar el precio de un producto en una sola tienda?**

El precio está vinculado al SKU del producto, por lo que aplica a todas las tiendas donde existe ese producto. Para precios diferentes por tienda, se puede crear el producto con un SKU distinto para cada una.

**¿Los descuentos se aplican por producto o por carrito?**

Los descuentos predefinidos se aplican sobre el subtotal total del carrito. Para descuentos por producto individual, el cajero puede editar el precio directamente al agregar el ítem al carrito.

**¿Las categorías son compartidas entre tiendas?**

Sí. Las categorías son globales para el comercio, no específicas por tienda. Todos los productos de todas las tiendas pueden usar las mismas categorías.

**¿La receta se puede usar con productos simples (no menú)?**

El módulo de recetas e insumos está diseñado para el Modo Restaurante. Para comercios de venta de productos terminados (sin elaboración), el sistema de lotes por compra es suficiente para controlar el costo de inventario.
