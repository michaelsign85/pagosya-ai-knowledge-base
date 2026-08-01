---
title: Facturación Electrónica SIAT
version: v1
audiencia: merchants
actualizado_en: 2026-07-06
---

# Facturación Electrónica SIAT

PagosYa está integrado en **producción** con el Sistema de Facturación Electrónica (SFE) del Servicio de Impuestos Nacionales (SIN) de Bolivia, en modalidad **Computarizada en Línea**. Desde el POS, el negocio puede emitir facturas con validez fiscal además de recibos comunes.

**Quién puede usarlo:** planes que incluyen facturación SIAT: **ExpandeYa** (50 facturas/mes), **ConquistaYa** (100/mes) y **RestauranteYa** (150/mes). EmprendeYa y Plan Checkout Web no incluyen esta función. Al agotar el cupo mensual del plan, se pueden comprar créditos para seguir facturando (ver Sección 5).

---

## Sección 1 — Onboarding: activar SIAT por primera vez

Este proceso se hace **una sola vez por negocio** (por NIT), desde **Configuraciones Avanzadas** (`/configuraciones`), en la tarjeta "Facturación Electrónica SIAT". Tiene 3 pasos con indicador visual de progreso.

### Paso 1 — Enviar la solicitud

El propietario completa un formulario con los datos fiscales del negocio:
- **NIT** de la empresa
- **Login SIAT** (usuario/email de su Oficina Virtual del SIN)
- **Correo electrónico** de contacto
- **Razón Social** (nombre fiscal registrado en el SIN)
- **Municipio**
- **Dirección** fiscal
- Teléfono (opcional)

Al hacer clic en **"Enviar Solicitud"**, los datos quedan guardados y la pantalla pasa al estado **"Asociación SIN"**.

### Paso 2 — Asociación manual del NIT (a cargo de PagosYa)

Con estos datos, el equipo de PagosYa asocia manualmente el NIT del negocio como contribuyente en el portal del SIN. Este paso no lo hace el usuario — es un trámite interno del equipo de soporte. Mientras se completa, la pantalla muestra "Solicitud enviada" con un resumen del NIT y Razón Social.

> No hay una duración fija — depende de la gestión con el SIN. El usuario puede volver a "Editar Solicitud" en cualquier momento si algún dato cambió.

### Paso 3 — Generar y guardar el Token Delegado

Una vez que PagosYa confirma la asociación, el usuario debe:

1. Entrar a su **Oficina Virtual del SIN**.
2. Generar un **Token Delegado** para el sistema **"PagosYA 3.2"**.
3. Volver a PagosYa → Configuraciones Avanzadas y completar:
   - **Sucursal** (número, por defecto 0)
   - **Punto de Venta** (número, por defecto 0)
   - **Número de Factura inicial** (solo la primera vez — si el negocio ya facturaba por otro medio con este NIT/Punto de Venta, aquí se indica el próximo número a continuar; en blanco arranca desde el 1)
   - **Token SIAT (Delegado)** — se pega el token generado en el paso anterior
4. Clic en **"Guardar y Activar"**.

> PagosYa trabaja únicamente con **modalidad Computarizada en Línea**, en ambiente de **Producción** — estas opciones no se muestran al usuario porque no hay otra alternativa.

El token se guarda **cifrado** (AES-256-GCM) — nunca se muestra en texto plano una vez guardado. Para cambiarlo, usar el botón "Editar credenciales".

### Paso 4 — Probar conexión

Con el token guardado, clic en **"Probar Conexión"**. El sistema valida las credenciales contra el SIN. Si falla, aparece un mensaje explicando la causa probable (token inválido/expirado, punto de venta inexistente, timeout del SIN, etc.) y un detalle técnico desplegable para soporte.

### Paso 5 — Sincronizar catálogo

Tras una conexión exitosa, aparece el botón **"Sincronizar"** (catálogo). Importa desde el SIN los catálogos oficiales necesarios para facturar: actividades económicas, productos/servicios y métodos de pago. Sin este paso, el sistema no puede resolver los códigos fiscales al emitir.

> Este mismo botón de sincronización también está disponible en **Facturas** (`/facturas`) como "Sincronizar Catálogos", por si se necesita repetir el proceso más adelante (ej: el SIN agrega nuevos códigos).

---

## Sección 2 — Configurar productos con datos fiscales

Cada producto que se vende con factura necesita 3 campos fiscales configurados en su ficha (Productos → crear/editar):

- **Código de producto SIN**
- **Código de actividad económica**
- **Unidad de medida SIN**

Estos campos tienen un buscador integrado: al escribir el nombre del producto, el sistema sugiere las opciones del catálogo oficial del SIN ya sincronizado.

**Son obligatorios.** El botón "Guardar"/"Actualizar" del producto queda deshabilitado hasta completarlos. Si un producto no los tiene (por ejemplo, fue creado antes de activar SIAT), el POS bloquea cualquier venta a factura que lo incluya — con un aviso indicando el nombre del producto — hasta que se complete su ficha.

---

## Sección 3 — Emitir una factura en el POS

1. Al cobrar, el cajero elige entre **Recibo** o **Factura**.
2. Si elige Factura, el sistema pide los datos del comprador: **NIT**, **Razón Social**, email (opcional) y complemento (opcional).
3. Para un cliente sin NIT específico, se usa el NIT genérico **0 / "S/N"** — emite una factura de consumidor final.
4. Confirmado el pago, la factura se envía al SIN y queda con estado **VALIDADA** (o **PENDIENTE** si se emitió en contingencia — ver Sección 4).

**Bloqueos automáticos antes de emitir:**
- **Datos fiscales incompletos** en algún producto del carrito → bloquea con aviso nominal, no permite ni iniciar la venta a factura.
- **Límite de facturas del plan agotado y sin créditos disponibles** → bloquea con aviso para comprar un paquete de créditos.

---

## Sección 4 — Modo Contingencia (facturación sin internet/SIAT caído)

Si el SIN o el internet del local fallan al momento de cobrar, el cajero puede activar manualmente **"Modo Contingencia"** en el modal de pago (ícono de WiFi tachado), eligiendo el motivo del evento:

| Evento | Motivo |
|--------|--------|
| 1 | Corte de Internet |
| 2 | Inaccesibilidad del sistema del SIN |
| 7 | Corte de Energía Eléctrica |

La venta se registra localmente con estado **PENDIENTE** — el negocio sigue vendiendo sin interrupción. Más tarde, desde **Facturas** (`/facturas`) → **"Sincronizar Offline"**, el sistema envía todas las facturas pendientes al SIN con sus CUFD correspondientes para validarlas retroactivamente.

---

## Sección 5 — Límites por plan y créditos adicionales

| Plan | Facturas SIAT incluidas/mes |
|------|------------------------------|
| EmprendeYa | No incluye |
| ExpandeYa | 50 |
| ConquistaYa | 100 |
| RestauranteYa | 150 |
| Plan Checkout Web | No incluye |

El sistema cuenta las facturas **VALIDADAS** emitidas en el mes calendario en curso. Al agotar el cupo del plan:

1. El sistema bloquea nuevas facturas con el aviso: *"Alcanzaste el límite de facturas SIAT de tu plan."*
2. El negocio compra créditos desde **Suscripción → Comprar Créditos** (Bs. 20 c/u).
3. Al usarlos, elige la opción **"Facturas SIAT"** — cada crédito agrega **+50 facturas** adicionales a un saldo extra que no vence (se consume solo al emitir facturas aceptadas, una por una, después de agotar el cupo gratis del plan).

Ver documento `10-creditos.md` para el detalle completo del sistema de créditos.

---

## Sección 6 — Gestionar facturas emitidas

Desde **Facturas** (`/facturas`):
- Listado con filtros por estado (VALIDADA, ANULADA, RECHAZADA, PENDIENTE, OBSERVADA), fecha y búsqueda.
- Tarjetas de resumen: total emitidas, total anuladas, monto facturado, monto anulado.
- Ver detalle de una factura: datos del emisor y comprador, ítems, QR de verificación, CUF.
- **Anular** una factura con motivo (Error de datos / Devolución total / Nota crédito-débito) y **Revertir anulación** si fue un error.
- **Reenviar por email** al comprador.
- **Imprimir** el comprobante.
- Exportar el listado a Excel.
- **Sincronizar Catálogos** y **Sincronizar Offline** (mismos botones descritos en las Secciones 1 y 4).

---

## Preguntas frecuentes

**¿Todos los planes pueden emitir facturas SIAT?**
No. Solo ExpandeYa, ConquistaYa y RestauranteYa las incluyen. EmprendeYa y Plan Checkout Web no tienen esta función habilitada.

**¿Qué pasa si cambio de NIT o de razón social?**
Debe gestionarse con soporte de PagosYa — el token delegado y la asociación están vinculados al NIT original registrado en el onboarding.

**¿El Token Delegado se puede ver una vez guardado?**
No. Se guarda cifrado y no se muestra en texto plano. Para cambiarlo, usar "Editar credenciales" y pegar uno nuevo generado desde la Oficina Virtual del SIN.

**¿Qué pasa si se me acaban las facturas del plan a mitad de mes?**
El sistema bloquea nuevas facturas hasta que se agregue saldo. Se soluciona comprando créditos (+50 facturas c/u) desde Suscripción — no es necesario esperar al siguiente mes ni cambiar de plan.

**¿Puedo facturar sin internet?**
Sí, activando manualmente el "Modo Contingencia" al cobrar. La venta queda pendiente hasta sincronizarla con el SIN apenas vuelva la conexión.

**¿Qué documentos fiscales emite PagosYa?**
Por ahora, solo factura de compra-venta (modalidad estándar). No se emiten notas de crédito-débito, facturas de exportación ni facturas con derecho a crédito fiscal como documentos independientes.
