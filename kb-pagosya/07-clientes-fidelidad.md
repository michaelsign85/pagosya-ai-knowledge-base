---
title: Gestión de clientes y programa de fidelidad
version: v3
audiencia: merchants
actualizado_en: 2026-05-23
---

# Gestión de clientes y programa de fidelidad

El módulo de **Clientes** centraliza toda la información de tus compradores: datos de contacto, historial de compras, métricas de comportamiento y saldo de puntos del programa de fidelidad. Está integrado con el POS, la tienda online y los reportes.

---

## Acceso al módulo

Desde el menú lateral hacer clic en **Clientes**. La pantalla muestra todos los clientes del negocio en tarjetas con sus métricas principales.

> El módulo de Clientes es accesible para el propietario y para empleados con el permiso de "Clientes" habilitado.

---

## Tarjeta de cliente

Cada cliente se muestra como una tarjeta con:
- **Nombre**
- **Puntos de fidelidad** acumulados (ícono de estrella amarilla)
- **Email**, **teléfono** y **dirección** (si fueron registrados)
- **Total gastado**: monto acumulado de todas sus compras
- **Visitas**: cantidad de veces que realizó una compra

**Acciones disponibles en cada tarjeta:**
- **Historial** (ícono de reloj): ver el historial completo de compras del cliente.
- **Editar** (ícono de lápiz): modificar los datos del cliente.
- **Eliminar** (ícono de papelera): eliminar el cliente del sistema.

---

## Buscar clientes

La barra de búsqueda en la parte superior permite buscar clientes por:
- Nombre
- Email
- Teléfono

La búsqueda es en tiempo real, filtrando la lista mientras se escribe.

---

## Crear un nuevo cliente

1. Hacer clic en **"Nuevo Cliente"** (botón azul en la esquina superior derecha).
2. Completar el formulario:
   - **Nombre** *(obligatorio)*
   - **Email** *(opcional)*
   - **Teléfono** *(opcional)*
   - **Dirección** *(opcional)*
   - **Puntos**: puntos de fidelidad iniciales (normalmente 0)
   - **Total Gasto**: monto histórico acumulado (normalmente 0)
   - **Visitas**: número de visitas históricas (normalmente 0)
3. Hacer clic en **"Crear"**.

> **Prevención de duplicados**: si se ingresa un email o teléfono que ya existe en la base de clientes, el sistema avisa que el cliente ya existe y actualiza sus datos en lugar de crear un duplicado.

---

## Editar un cliente

1. Hacer clic en el ícono de **lápiz** en la tarjeta del cliente.
2. Modificar los campos necesarios.
3. Hacer clic en **"Actualizar"**.

Es posible editar manualmente los puntos de fidelidad, el total gastado y el conteo de visitas para correcciones o migraciones de datos históricos.

---

## Eliminar un cliente

1. Hacer clic en el ícono de **papelera** en la tarjeta del cliente.
2. Confirmar la eliminación en el mensaje de confirmación.

> La eliminación es permanente. Si el cliente tiene historial de compras, esas ventas quedarán sin cliente asignado en los reportes.

---

## Historial de compras del cliente

Hacer clic en el ícono de **historial** (reloj) abre el **Historial de Compras** del cliente, con:

### Métricas resumidas

| Métrica | Descripción |
|---------|-------------|
| **Total Gastado** | Suma de todas sus compras en Bs. |
| **Compras** | Número total de transacciones |
| **Puntos** | Saldo actual de puntos de fidelidad |
| **Ticket Promedio** | Promedio por compra (Total Gastado ÷ Compras) |

### Lista de compras

Cada compra muestra:
- Número de compra (ID)
- Fecha y hora
- Monto total
- Estado (completada, cancelada)
- Productos comprados (si están registrados en la venta)

---

## Asignar un cliente en el POS

Al realizar una venta en el POS, es posible asociar el cliente:
1. En la pantalla de cobro, buscar el cliente por nombre, teléfono o CI en el campo de cliente.
2. El sistema muestra el nombre del cliente y su **saldo de puntos disponibles**.
3. Si el programa de fidelidad está activo, al completar la venta los puntos se acumulan automáticamente.

> Ver más detalles en la documentación del **POS → Asignación de cliente y fidelidad**.

---

## Programa de fidelidad por puntos

El programa de fidelidad incentiva la recompra recompensando a los clientes con puntos por cada compra, que luego pueden canjear como descuento en futuras ventas.

### Cómo funciona

1. El cliente realiza una compra.
2. El sistema calcula los puntos ganados según el **porcentaje configurado**.
3. Los puntos se acreditan automáticamente en la cuenta del cliente.
4. En una próxima compra, el cliente puede **canjear** sus puntos por descuento.

**Conversión de canje**: 10 puntos = Bs. 1 de descuento.

**Ejemplo completo:**
- Configuración: 5% de puntos
- Compra de Bs. 200 → el cliente gana **10 puntos**
- En la siguiente visita, canjea 10 puntos → obtiene **Bs. 1** de descuento

### Configurar el programa de fidelidad

1. Ir a **Clientes**.
2. Hacer clic en el botón naranja **"Fidelidad"** (ícono de engranaje).
3. En el modal de **Configuración de Fidelidad**:
   - **Estado del Programa**: activar o desactivar el programa con el checkbox.
   - **Porcentaje de puntos**: ingresar el porcentaje del monto de compra que se convierte en puntos (entre 0% y 100%).
4. Ver el **ejemplo en tiempo real** que muestra cuántos puntos recibirá el cliente por compras típicas.
5. Hacer clic en **"Guardar"**.

**Ejemplo de configuración:**
- 2% → en una compra de Bs. 100, el cliente gana 2 puntos
- 5% → en una compra de Bs. 100, el cliente gana 5 puntos
- 10% → en una compra de Bs. 100, el cliente gana 10 puntos

> Cuando el programa está **inactivo**, no se acumulan puntos en las ventas. Los puntos existentes de los clientes se conservan y pueden canjearse igualmente.

### Canjear puntos en el POS

Cuando un cliente tiene puntos acumulados:
1. En el POS, asignar el cliente a la venta.
2. El sistema detecta el saldo de puntos disponibles.
3. En la pantalla de cobro aparece la opción **"Canjear Puntos"**.
4. Se abre el modal de **Canjear Puntos** mostrando:
   - Nombre del cliente
   - Puntos disponibles
   - Campo para ingresar la cantidad de puntos a canjear
   - **Opciones rápidas**: 25%, 50%, 75% o "Todos" los puntos disponibles
   - Descuento en Bs. que corresponde a los puntos ingresados
5. Confirmar el canje. El descuento se aplica automáticamente al total de la venta.

**Límite**: no se pueden canjear más puntos de los que el cliente tiene disponibles.

El canje de puntos queda registrado en el detalle del cupón y es visible en el módulo de Cupones (columna "Puntos canjeados" y "Descuento por puntos").

---

## Integración con reportes

Los clientes asignados a ventas aparecen en:
- **Reportes de Ventas**: columna "Cliente" en la tabla de transacciones.
- **Ventas por Funcionarios**: columna "Clientes únicos" (cantidad de clientes distintos atendidos por cada empleado).
- **Cupones**: campo "Cliente" en el detalle de cada cupón, junto con los puntos canjeados.

---

## Preguntas frecuentes

**¿Los clientes son compartidos entre tiendas?**

No. Cada tienda tiene su propia base de clientes. Si el negocio tiene múltiples tiendas, cada una gestiona sus propios clientes por separado.

**¿Los puntos se acumulan en todas las tiendas?**

Los puntos están ligados a la tienda donde se realizó la compra. Cada tienda tiene su configuración de fidelidad independiente.

**¿Qué pasa con los puntos si cancelo una venta?**

Si se cancela un cupón, los puntos que fueron acreditados por esa venta no se revierten automáticamente. Si es necesario, ajustar el saldo de puntos del cliente manualmente desde la pantalla de edición del cliente.

**¿Puedo importar clientes desde otro sistema?**

No hay importación masiva por CSV desde la interfaz en esta versión. Los clientes pueden crearse uno a uno o se agregan automáticamente al realizar ventas en el POS cuando se asigna el cliente.

**¿Un cliente creado en el POS también aparece en la lista de Clientes?**

Sí. Cualquier cliente asignado en el POS queda registrado automáticamente en la base de clientes del módulo.

**¿Puedo ajustar los puntos de un cliente manualmente?**

Sí. Desde el botón "Editar" del cliente es posible modificar directamente el campo "Puntos" para correcciones o bonificaciones especiales.

**¿Cuántos clientes puedo registrar?**

No hay límite en la cantidad de clientes. La base de datos crece conforme el negocio opera.
