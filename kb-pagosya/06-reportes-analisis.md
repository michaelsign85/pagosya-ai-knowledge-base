---
title: Reportes y análisis
version: v3
audiencia: merchants
actualizado_en: 2026-05-23
---

# Reportes y análisis

PagosYa registra cada venta, turno y movimiento de caja de forma automática. Toda esa información se organiza en **6 módulos de reportes** accesibles desde el ícono de gráfico en el menú lateral. Los reportes se actualizan en tiempo real y pueden exportarse en PDF o CSV.

> Los reportes son accesibles para el **propietario** y para los **empleados** con permiso de "Reportes" habilitado.

---

## Acceso a los reportes

1. Hacer clic en el ícono de **Reportes y Análisis** en el menú lateral.
2. Se abre el selector con los 6 módulos disponibles:
   - Reportes de Ventas
   - Ventas por Artículos
   - Ventas por Funcionarios
   - Ventas por Categorías
   - Cupones
   - Turnos
3. Seleccionar el reporte deseado.

**Filtros comunes** disponibles en todos los reportes:
- **Período**: selector de rango de fechas con calendario visual.
- **Tienda**: filtrar por una tienda específica o ver todas las tiendas.
- **Empleado**: filtrar por un empleado específico o todos.

---

## 1. Reportes de Ventas

El reporte principal del negocio. Muestra el **análisis general de ventas y rendimiento** del período seleccionado.

### Métricas principales

| Métrica | Descripción |
|---------|-------------|
| **Total de Ventas** | Suma total en Bs. de todas las transacciones en el período |
| **Promedio por Venta** | Ticket promedio: Total ÷ número de transacciones |
| **Ventas del Día** | Total vendido en el día de hoy |
| **Número de transacciones** | Cantidad de ventas completadas |

### Gráfico de ventas por día

Muestra un **gráfico de área** con la evolución de las ventas día a día en el período seleccionado. Útil para identificar tendencias, picos de venta y días con baja actividad.

### Tabla de transacciones

Lista detallada de cada venta con:
- Fecha y hora
- Tienda
- Empleado
- Cliente (si fue asignado)
- Canal de venta: **POS**, **Venta Rápida**, **Tienda Online**, **Manual**
- Método de pago
- Monto total
- Estado (completada, reembolsada, etc.)

La tabla muestra **10 registros por página** con navegación.

### Exportación

- **Exportar CSV**: descarga un archivo con todas las transacciones del filtro activo.
- **Exportar PDF**: genera un PDF con el resumen, métricas y gráfico incluido.

---

## 2. Ventas por Artículos

Análisis detallado de **qué productos se vendieron** en el período. Permite identificar los productos más rentables, los de baja rotación y las oportunidades de ajuste de precios o compras.

### Métricas por producto

| Métrica | Descripción |
|---------|-------------|
| **Artículos vendidos** | Cantidad total de unidades vendidas del producto |
| **Ventas líquidas** | Total en Bs. generado por ese producto |
| **Costo de mercancía** | Costo total basado en el costo del producto × unidades vendidas |
| **Lucro bruto** | Ventas líquidas − costo de mercancía |
| **Margen %** | Porcentaje de ganancia sobre el precio de venta |

### Cómo leer este reporte

- Los productos con **margen alto** y **alto volumen** son los más rentables.
- Los productos con **margen alto** pero **bajo volumen** pueden necesitar más visibilidad o promoción.
- Los productos con **margen bajo** y **bajo volumen** son candidatos a revisar precio o eliminar del catálogo.

### Filtros adicionales

Además de período y tienda, permite filtrar por:
- **Categoría**: ver solo los artículos de una categoría específica.

### Exportación

- **Exportar CSV**: tabla completa de artículos con todas las métricas.
- **Exportar PDF**: informe con gráfico de barras de los productos más vendidos.

---

## 3. Ventas por Funcionarios

Reporte de **rendimiento individual del equipo de ventas**. Muestra cuánto vendió cada empleado en el período, con desglose completo.

### Métricas por empleado

| Métrica | Descripción |
|---------|-------------|
| **Ventas Brutas** | Total en Bs. vendido por el empleado |
| **Reembolsos** | Monto de ventas revertidas/canceladas |
| **Descuentos** | Total en descuentos aplicados por el empleado |
| **Ventas Netas** | Ventas Brutas − Reembolsos − Descuentos |
| **Cupones** | Cantidad de transacciones (ventas) realizadas |
| **Cantidad de productos** | Número total de ítems vendidos |
| **Gasto promedio** | Ticket promedio del empleado |
| **Clientes únicos** | Clientes distintos atendidos en el período |

### Cómo leer este reporte

- Comparar las **ventas netas** entre empleados para identificar el mejor rendimiento.
- El **gasto promedio** indica si el empleado logra ventas de mayor valor.
- Los **descuentos aplicados** pueden revelar si hay patrones de uso excesivo de descuentos.
- Si un empleado tiene muchos **reembolsos**, puede ser señal de problemas en el proceso de venta.

### Vista por tienda

Si el empleado trabaja en más de una tienda, el reporte muestra una fila por cada combinación empleado + tienda.

### Exportación

- **Exportar CSV**: tabla con todos los empleados y métricas.
- **Exportar PDF**: informe con el listado de empleados y sus resultados.

---

## 4. Ventas por Categorías

Análisis de rendimiento **agrupado por categoría de productos**. Muestra qué familias de productos generan más ingresos.

### Métricas por categoría

| Métrica | Descripción |
|---------|-------------|
| **Artículos vendidos** | Total de unidades vendidas en la categoría |
| **Ventas líquidas** | Total en Bs. generado por la categoría |
| **Custodio de mercancías** | Costo total de los productos vendidos en la categoría |
| **Lucro bruto** | Ventas líquidas − custodio de mercancías |

### Gráfico de barras

Visualización gráfica de las categorías ordenadas por volumen de ventas. Cada categoría tiene un color asignado automáticamente para facilitar la lectura.

### Filtros adicionales

- **Categoría**: ver el detalle de una sola categoría o todas.

### Cómo leer este reporte

- Las categorías con **mayor lucro bruto** son las más estratégicas para el negocio.
- Las categorías con **bajo volumen** pueden necesitar más variedad de productos o mejor visibilidad en el POS.

### Exportación

- **Exportar CSV**: datos de todas las categorías.
- **Exportar PDF**: informe con gráfico de barras incluido.

---

## 5. Cupones (historial de ventas)

Registro completo de **todas las transacciones del negocio**, con información detallada de cada venta individual. Este módulo funciona como el historial central de comprobantes.

### Qué muestra

- **Número de cupón**: identificador único de la venta.
- **Fecha y hora** de la transacción.
- **Tienda** donde se realizó.
- **Empleado** que atendió (y quién cerró la caja, si son diferentes).
- **Canal de venta**: POS, Venta Rápida, Tienda Online.
- **Cliente** (si fue asignado).
- **Método de pago**: efectivo, QR, tarjeta débito/crédito, transferencia, mixto.
- **Subtotal**, **descuentos aplicados** y **total final**.
- **Estado**: completada, cancelada, reembolsada.

### Métricas del período

En la parte superior se muestran:
- **Total de cupones** (cantidad de transacciones).
- **Total en ventas** (monto total Bs.).
- **Total de descuentos** aplicados.

### Ver detalle de una venta

Hacer clic en el ícono de ojo (👁) de cualquier cupón para abrir el **detalle completo**:
- Lista de productos con cantidad y precio unitario.
- Desglose de descuentos (nombre, tipo y monto de cada descuento).
- Puntos de fidelidad canjeados (si aplica).
- Información del empleado que atendió vs. el que cerró la caja.
- Nombre del pedido guardado (si fue cargado desde órdenes abiertas).

### Imprimir un cupón

Desde el detalle de la venta, hacer clic en **"Imprimir"**:
- En la **app móvil**: envía a la impresora térmica configurada.
- En la **web**: abre el diálogo de impresión del navegador.

### Cancelar un cupón

El **propietario** o cualquier **empleado con permiso de acceso al módulo Cupones** puede cancelar una venta ya registrada.

**Cómo cancelar:**
1. Buscar el cupón en la lista (por número, cliente o empleado).
2. Hacer clic en el botón rojo **"Cancelar Cupón"** dentro del detalle del cupón, o en el ícono de cancelar (🚫) directamente desde la lista.
3. Confirmar la cancelación en el modal de confirmación.

**Qué ocurre al cancelar un cupón:**
- El estado de la venta cambia a **"cancelada"**.
- El cupón sigue visible en el historial con estado cancelado (nunca se elimina).
- El monto de la venta **ya no se contabiliza** en los totales de los reportes de ventas del período.
- En el reporte de Ventas por Funcionarios, los reembolsos/cancelaciones del empleado se reflejan en la columna "Reembolsos".
- El stock **no se ajusta automáticamente**: si los productos deben volver al inventario, el encargado debe hacer el ajuste manualmente desde la pantalla de Productos.

> **Importante:** La cancelación es irreversible. Una vez cancelado, el cupón no puede reactivarse. Si fue un error, se debe registrar una nueva venta.

### Búsqueda y filtros

- **Búsqueda libre**: buscar por número de cupón, nombre de cliente o empleado.
- **Período**: rango de fechas.
- **Tienda** y **empleado**.
- **Paginación configurable**: 10, 25, 50 o 100 registros por página.

### Exportación

- **Exportar CSV**: todas las ventas del período con cada campo.
- **Exportar PDF**: listado con las métricas del período.

---

## 6. Turnos

Control detallado de **apertura y cierre de caja por turno**. Permite revisar el historial de jornadas de trabajo de cada empleado, la conciliación de caja y los movimientos durante el turno.

### Qué muestra cada turno

| Campo | Descripción |
|-------|-------------|
| **Empleado** | Quién abrió el turno |
| **Tienda** | En qué sucursal fue el turno |
| **Fecha de apertura** | Fecha y hora de inicio del turno |
| **Fecha de cierre** | Fecha y hora en que se cerró (o "Abierto" si sigue activo) |
| **Duración** | Tiempo total del turno |
| **Monto de apertura** | Efectivo declarado al abrir la caja |
| **Monto de cierre** | Efectivo declarado al cerrar la caja |
| **Diferencia** | Monto de cierre − monto de apertura (puede ser positivo o negativo) |
| **Ventas del turno** | Cantidad de ventas realizadas en el turno |
| **Total de ventas** | Monto total en Bs. vendido durante el turno |
| **Estado** | Abierto / Cerrado |

### Ver detalle del turno

Hacer clic en el ícono de detalle de cualquier turno para ver:

**Resumen del turno:**
- Todas las métricas del turno.
- Indicador de diferencia de caja (positivo = sobrante, negativo = faltante).

**Movimientos de caja:**
- Lista de **suprimentos** (entradas de efectivo) y **sangrias** (retiros de efectivo) realizados durante el turno, con monto, motivo y hora.

**Ventas del turno:**
- Lista de todas las ventas realizadas en ese turno, con ítems, método de pago y monto.

### Imprimir el cierre de turno

Al finalizar el turno, el empleado puede imprimir el **reporte de cierre de caja** desde el detalle del turno:

1. Abrir el detalle del turno que fue cerrado.
2. Hacer clic en **"Imprimir"**.
   - En la **app móvil**: envía el reporte directamente a la impresora térmica.
   - En la **web**: abre el diálogo de impresión del navegador.

**Qué incluye el reporte impreso de cierre de turno:**
- Nombre del empleado y tienda.
- Fecha y hora de apertura y cierre.
- Monto declarado al abrir y al cerrar la caja.
- Diferencia de caja (sobrante o faltante).
- Lista de movimientos: suprimentos (entradas) y sangrias (retiros).
- Total de ventas del turno y cantidad de cupones.

**Proceso de auditoría recomendado:**

El reporte impreso debe ser **firmado por el empleado** que realizó el turno como constancia de los montos declarados. Luego debe ser **entregado al propietario o administrador**, quien también firma como constancia de haber recibido y verificado el cierre de caja.

Este documento físico queda como respaldo de auditoría interna del comercio.

> El propietario o administrador puede comparar el monto de cierre declarado por el empleado con el total de ventas registradas en el sistema para verificar que no haya diferencias no justificadas.

### Filtros

- **Período**: rango de fechas.
- **Tienda** y **empleado**.
- **Búsqueda libre**: por nombre de empleado o tienda.
- **Registros por página**: configurable (25 por defecto).

### Exportación

- **Exportar PDF**: listado de turnos con sus métricas principales.

---

## Consideraciones de acceso por rol

| Rol | Acceso |
|-----|--------|
| **Propietario** | Acceso completo a todos los reportes de todas las tiendas |
| **Administrador** | Acceso completo según configuración |
| **Gerente** | Acceso según el permiso "Reportes" habilitado por el propietario |
| **Caja** | Sin acceso a reportes por defecto |

> Los empleados solo ven datos de las tiendas en las que tienen asignación. No pueden ver datos de otras tiendas del comercio.

---

## Preguntas frecuentes

**¿Los reportes se actualizan en tiempo real?**

Sí. Cada vez que se completa una venta, el sistema registra la transacción y los datos quedan disponibles inmediatamente en todos los reportes.

**¿Puedo ver reportes de períodos muy antiguos?**

Sí. No hay límite de antigüedad en los reportes. El selector de fechas permite elegir cualquier rango histórico.

**¿El reporte de categorías requiere que los productos estén asignados a una categoría?**

Para que un producto aparezca en el reporte de Ventas por Categorías, debe tener al menos una categoría asignada. Los productos sin categoría no se agrupan en este reporte.

**¿La cancelación de un cupón afecta los reportes?**

Sí. Los cupones cancelados aparecen con estado "cancelada" en el historial. Los reportes de ventas muestran las ventas según su estado, por lo que las canceladas pueden separarse de las completadas.

**¿Un empleado puede ver sus propias ventas?**

Sí, si el propietario le habilita el permiso de reportes. El empleado verá únicamente los datos de las tiendas en las que trabaja.

**¿La exportación CSV incluye todos los datos o solo los visibles?**

La exportación incluye todos los registros que corresponden al filtro activo (fecha, tienda, empleado), independientemente de la página que esté visible en pantalla.
