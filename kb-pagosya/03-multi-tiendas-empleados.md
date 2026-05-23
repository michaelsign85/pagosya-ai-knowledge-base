---
title: Múltiples tiendas y gestión de empleados
version: v3
audiencia: merchants
actualizado_en: 2026-05-22
---

# Múltiples tiendas y gestión de empleados

PagosYa permite operar varias sucursales y gestionar un equipo de trabajo desde una sola cuenta. Cada tienda tiene su propio POS, caja, inventario y empleados asignados. El propietario puede supervisar todo desde un único acceso sin necesidad de estar presente en cada local.

---

## Gestión de tiendas

### Cuántas tiendas puedo tener

El número de tiendas disponibles depende del plan activo:

| Plan | Tiendas incluidas |
|------|-------------------|
| EmprendeYa | 1 |
| ExpandeYa | 3 |
| ConquistaYa | 6 |
| RestauranteYa | 6 |
| Checkout Web | 1 |

Si el negocio crece y necesita más tiendas de las que incluye el plan, se pueden agregar tiendas adicionales mediante **créditos** desde Configuraciones → Créditos.

---

### Cómo crear una tienda

1. Ir a **Configuraciones → Tiendas**.
2. Hacer clic en **"Nueva tienda"**.
3. Completar los datos:
   - **Nombre** de la sucursal
   - **Dirección** física del local
   - **Teléfono** de contacto (opcional)
   - **Logo** de la tienda (opcional, se muestra en reportes y comprobantes)
4. Guardar.

La tienda queda activa inmediatamente y puede usarse desde el POS, reportes y asignación de empleados.

---

### Para qué sirve la geolocalización de la tienda

La geolocalización (geocerca) es una función de seguridad opcional que permite **verificar que el empleado esté físicamente en el local** antes de poder abrir o cerrar caja.

**Cómo funciona:**
- El propietario configura las coordenadas GPS del local y un radio permitido (en metros).
- Cuando un empleado intenta abrir caja, el sistema verifica su ubicación.
- Si está dentro del radio configurado, puede continuar normalmente.
- Si está fuera del radio, el sistema muestra un aviso y puede bloquear la apertura.

**Por qué configurarla:**
- Evita que empleados abran o cierren caja desde otro lugar.
- Reduce el riesgo de registros falsos o manipulados.
- Permite mayor control en negocios con varios locales.

> La geocerca está **deshabilitada por defecto**. El propietario puede activarla por tienda desde Configuraciones → Tiendas → seleccionar la tienda → Geocerca.

**Cómo configurar la geocerca:**
1. Ir a Configuraciones → Tiendas.
2. Seleccionar la tienda.
3. Ingresar a la sección **Geocerca**.
4. Activar la geocerca.
5. El mapa muestra la ubicación actual o ingresada. Ajustar el punto central al local físico.
6. Definir el radio en metros (por ejemplo: 100 metros).
7. Guardar.

---

### Editar o eliminar una tienda

- **Editar**: desde Configuraciones → Tiendas → seleccionar la tienda → modificar los datos → Guardar.
- **Eliminar**: disponible solo si la tienda no tiene cajas abiertas ni transacciones activas. El sistema lo impide si hay datos pendientes.

---

## Gestión de empleados

### Cuántos empleados puedo agregar

El número de empleados también depende del plan:

| Plan | Empleados incluidos |
|------|---------------------|
| EmprendeYa | 1 |
| ExpandeYa | 3 |
| ConquistaYa | 6 |
| RestauranteYa | 6 |
| Checkout Web | 1 |

Si se necesitan más empleados, se pueden agregar con créditos adicionales.

---

### Cómo agregar un empleado

El sistema usa un flujo de **invitación por correo electrónico**. El empleado recibe un enlace para crear su propia contraseña.

**Pasos para el propietario:**
1. Ir a **Configuraciones → Empleados**.
2. Hacer clic en **"Nuevo empleado"**.
3. Completar:
   - **Nombre completo**
   - **Correo electrónico** del empleado
   - **Cargo** (Administrador, Gerente o Cajero — ver sección de permisos)
   - **Tiendas** asignadas (puede asignarse a una o varias tiendas)
4. Confirmar. El sistema envía automáticamente un correo de invitación al empleado.

> El empleado queda en estado **pendiente** hasta que complete la activación.

---

### Cómo el empleado activa su cuenta y crea su contraseña

1. El empleado recibe un correo de PagosYa con un enlace de invitación.
2. Hace clic en el enlace (o lo copia en el navegador).
3. Se abre una página para **crear la contraseña** de su cuenta.
4. El empleado ingresa y confirma su contraseña.
5. La cuenta queda activada.
6. El empleado puede ingresar desde **pagosya.com.bo** o la app con su correo y la contraseña que creó.

> Si el empleado no recibe el correo, el propietario puede reenviar la invitación desde Configuraciones → Empleados → seleccionar el empleado.

---

### Cómo el empleado inicia sesión

El empleado inicia sesión desde la misma pantalla de acceso que el propietario (`/auth`):
- **Correo**: el que el propietario registró en el sistema.
- **Contraseña**: la que el empleado definió al activar su cuenta.

Al ingresar, el sistema detecta automáticamente que es un empleado y carga solo las funciones a las que tiene acceso según su cargo y las tiendas asignadas.

---

### Bloqueo y reactivación de empleados

- El propietario puede **desactivar** un empleado en cualquier momento desde Configuraciones → Empleados → seleccionar → desactivar.
- Un empleado desactivado no puede iniciar sesión ni operar el sistema.
- El empleado puede ser **reactivado** por el propietario cuando sea necesario.

---

## Permisos y accesos por cargo

PagosYa tiene tres niveles de cargo para empleados. El propietario tiene acceso total y no está limitado por permisos.

### Administrador

Acceso amplio, casi equivalente al propietario. Puede gestionar la operación diaria completa.

**Puede acceder a:**
- POS y ventas
- Caja (apertura y cierre)
- Productos e inventario
- Clientes y fidelidad
- Reportes de ventas
- Historial de cajas
- Configuración básica de la tienda

**No puede acceder a:**
- Gestión de otras tiendas (configuración de sucursales)
- Agregar o modificar empleados
- Configuración de integraciones bancarias
- Planes y facturación de la cuenta

---

### Gerente

Acceso operativo completo para el día a día, pero sin acceso a módulos de configuración avanzada.

**Puede acceder a:**
- POS y ventas
- Caja
- Productos e inventario
- Clientes
- Reportes básicos

**No puede acceder a:**
- Configuración de tiendas
- Gestión de empleados
- Tienda online
- Módulos de integración
- Reportes avanzados de administración

---

### Cajero (Caixa)

Acceso mínimo enfocado solo en el cobro diario.

**Puede acceder a:**
- POS para registrar ventas
- Apertura y cierre de caja
- Consulta básica de clientes

**No puede acceder a:**
- Productos e inventario (edición)
- Reportes
- Cualquier módulo de configuración
- Tienda online
- Empleados

---

### Permisos personalizados

Además del cargo base, el propietario puede **personalizar los permisos** de cada empleado individualmente, habilitando o deshabilitando el acceso a módulos específicos. Esto permite adaptar el acceso exactamente a las necesidades del negocio.

Para personalizar: Configuraciones → Empleados → seleccionar el empleado → Permisos.

---

## Asignación de empleados a tiendas

Un empleado puede estar asignado a **una o varias tiendas**. Cuando el empleado inicia sesión, puede seleccionar en qué tienda está trabajando.

- La asignación se hace al crear el empleado o editando sus datos después.
- Si el empleado tiene asignada una sola tienda, el sistema la carga automáticamente.
- Si tiene varias, el empleado selecciona la tienda activa al inicio del turno.
- Un empleado solo puede tener **una caja abierta a la vez**, independientemente de las tiendas asignadas.

---

## Control de caja por empleado

Cada empleado registra su turno mediante la apertura y cierre de caja.

### Apertura de caja
1. El empleado inicia sesión.
2. Va a la sección **Caja**.
3. Si la geocerca está activada, el sistema verifica la ubicación.
4. Ingresa el monto inicial en efectivo.
5. La caja queda abierta y registra todas las ventas del turno.

### Cierre de caja
1. Al terminar el turno, el empleado va a **Caja → Cerrar caja**.
2. Ingresa el monto final en efectivo.
3. El sistema muestra el resumen del turno: ventas por método de pago, total cobrado, diferencia de efectivo.
4. El empleado confirma el cierre.
5. El turno queda guardado en el historial.

> El propietario puede ver todos los turnos desde **Reportes → Historial de cajas**, filtrado por tienda, empleado o fecha.

---

## Gestión de turnos y asistencia

PagosYa registra automáticamente los turnos de los empleados basándose en la apertura y cierre de caja.

### Qué registra el sistema por turno:
- Empleado que abrió y cerró
- Tienda donde trabajó
- Hora de apertura y cierre
- Monto inicial y final en efectivo
- Total de ventas del turno
- Ventas por método de pago (efectivo, QR, tarjeta, etc.)
- Diferencia entre lo esperado y lo registrado

### Dónde consultar el historial de turnos:
- El propietario va a **Reportes → Turnos** (o Historial de Cajas).
- Puede filtrar por tienda, empleado o rango de fechas.
- Puede exportar o ver el resumen de cada turno.

> Este historial sirve como registro de asistencia basado en actividad real: si el empleado abrió y cerró caja, hay evidencia del tiempo trabajado.

---

## Reportes por tienda y por empleado

El sistema ofrece reportes segmentados para entender el rendimiento de cada sucursal y cada persona.

**Reportes disponibles:**
- Ventas totales por tienda (día, semana, mes)
- Comparación de desempeño entre tiendas
- Ventas registradas por empleado
- Historial de turnos por empleado
- Métodos de pago usados por tienda

> Para más detalle sobre reportes, ver la documentación **06-reportes-analisis.md**.

---

## Preguntas frecuentes

**¿El empleado puede ver las ventas de otras tiendas?**

No. Cada empleado solo tiene acceso a las tiendas que le asignó el propietario. Los datos de otras sucursales no son visibles.

**¿Un empleado puede cambiar su propia contraseña?**

Sí. Desde la configuración de su perfil dentro del sistema puede actualizar su contraseña.

**¿Qué pasa si el empleado olvida su contraseña?**

Puede usar la opción "Olvidé mi contraseña" en la pantalla de login para recibir un enlace de recuperación en su correo.

**¿Puedo tener varios cajeros abriendo caja en la misma tienda al mismo tiempo?**

Sí, pero cada cajero maneja su propia caja. Las ventas quedan separadas por empleado. Solo un empleado puede tener una caja abierta a la vez desde el mismo usuario.

**¿La geocerca funciona en la app móvil?**

Sí. Tanto en la versión web como en la app móvil, al intentar abrir caja el sistema solicita permiso de ubicación para verificar la geocerca si está activada.

**¿Qué pasa si el empleado está fuera del radio de la geocerca?**

El sistema muestra una advertencia. Dependiendo de la configuración del propietario, puede bloquearse completamente la apertura de caja o solo mostrar el aviso. El propietario puede ajustar este comportamiento desde la configuración de la geocerca.
