---
title: "CobraYa Condominios"
version: 1.1
audiencia: "merchants, agents, support"
actualizado_en: 2026-08-12
---

CobraYa Condominios es el **plan de PagosYa especializado para la administración de condominios, edificios y urbanizaciones**. Es un plan distinto de [CobraYa — Cobros Mensualizados](32-cobraya-cobros-mensualizados.md), dirigido a un público distinto (condominios, no academias/gimnasios/colegios). Incluye **todo** lo que trae CobraYa (cobranza recurrente de expensas, QR bancario sin comisión, portal del cliente, WhatsApp CRM oficial) y agrega encima un **módulo completo de gestión condominial**: residentes, comunicados, reservas de áreas comunes, contabilidad, control de visitas y encomendas — más un **app nativo "CobraYa" para los moradores** con notificaciones push gratuitas.

> 📄 La parte de cobranza (dashboard `/cobros`, clientes, planes, QR bancario, portal de pago, WhatsApp CRM) funciona **igual** que en CobraYa base — ver [32-cobraya-cobros-mensualizados.md](32-cobraya-cobros-mensualizados.md). Este documento cubre **solo lo adicional** del plan Condominios y cómo se conecta con el resto.

---

## 🎯 ¿Qué resuelve?

| Problema | Solución CobraYa Condominios |
|----------|------------------------------|
| Planillas de Excel para saber quién vive en cada unidad | Registro estructurado de unidades y residentes (propietarios, inquilinos, familiares, mascotas, vehículos) |
| Avisos que se pierden en grupos de WhatsApp | Comunicados con público segmentado (todo el condominio, una torre/grupo o una unidad) + notificación push |
| Reservar el salón de eventos o la parrilla a mano alzada | Sistema de reservas con calendario, tarifa y pago QR integrado |
| Rendición de cuentas del directorio poco clara | Contabilidad con ingresos/gastos, gastos fijos recurrentes y reporte mensual profesional (PDF) |
| Portería sin registro de quién entra y sale | Control de visitas con QR de acceso generado por el residente y escaneado por el portero |
| Paquetes que se entregan a la persona equivocada | Encomendas con destinatario específico y código de retiro de 4 dígitos que solo el residente conoce |
| Costo de WhatsApp y riesgo de baneo por mensajes masivos | App nativo con **push gratuito** como canal principal de avisos y recordatorios de pago |

---

## 📦 Plan y precio

CobraYa Condominios es **un plan superior y separado de CobraYa**: incluye todo CobraYa (cobranza recurrente, QR bancario, portal, validación de pagos y WhatsApp CRM oficial) y además el módulo condominial completo.

| Plan | Unidades activas | Volumen/mes | Usuarios/agentes | Mensal | Anual |
|------|------------------|-------------|------------------|---------|-------|
| **Condominios 100** | Hasta 100 | Bs. 100.000 | 3 | Bs. 449 | Bs. 4.490 |
| **Condominios 300** ⭐ | Hasta 300 | Bs. 300.000 | 5 | Bs. 699 | Bs. 6.990 |
| **Condominios 600** | Hasta 600 | Bs. 600.000 | 10 | Bs. 999 | Bs. 9.990 |
| **Condominios 1000** | Hasta 1.000 | Bs. 1.000.000 | 15 | Bs. 1.399 | Bs. 13.990 |
| **Corporativo** | +1.000 | Personalizado | Personalizado | Cotizar | — |

> El plan anual equivale a pagar 10 meses y recibir 12.

**Se factura por unidad ACTIVA, no por residente.** Un departamento con cinco personas cuenta como una unidad. Un trigger en la base de datos (`enforce_condo_unit_limit`) bloquea activar más unidades de las que permite el plan contratado.

Los cuatro planes por tramo se contratan desde `/planes` y van directo al checkout. Solo el Corporativo pasa por el equipo comercial. Incluyen las features `monthly_billing` (CobraYa base) + `condominios` (módulo condominial); **no incluyen** POS, productos ni tienda online.

> ⚠️ **No vendas Condominios como "X unidades por Bs. X".** Lo que se vende es la administración completa: expensas automáticas, pagos con QR, portal y app del residente, comunicados, reservas de áreas comunes, visitas, encomiendas y contabilidad del condominio.

---

## 🧱 Estructura del módulo

### Entidades principales

| Entidad | ¿Qué es? | Ejemplo |
|---------|---------|---------|
| **Unidad** (`condo_units`) | Departamento, casa o local dentro del condominio | "Torre A — Depto 302" |
| **Grupo / Torre** (`grupos_cobro`) | Agrupación de unidades (comparte con el sistema de cobros) | "Torre A", "Torre B" |
| **Residente** (`condo_residents`) | Persona (o mascota/vehículo) vinculada a una unidad | Jimena Ríos — propietaria, responsable de pago |
| **Vinculado** | Familiar, mascota o vehículo sin cobro propio, ligado al responsable de pago | Hijo de Jimena, perro "Toby" |
| **Comunicado** | Aviso publicado por la administración | "Reunión de propietarios — 15/07" |
| **Área común** | Espacio reservable con tarifa opcional | Salón de eventos, parrilla, cancha |
| **Reserva** | Solicitud de uso de un área en fecha/hora | Parrilla — sábado 10:00-14:00 |
| **Transacción contable** | Ingreso o gasto del condominio | Pago de luz de áreas comunes — Bs.450 |
| **Reporte mensual** | Reporte contable generado (borrador/publicado) | Reporte de julio 2026 |
| **Visita** | Registro de acceso de un tercero | "Juan Pérez visita Depto 302" |
| **Encomienda** | Paquete recibido en portería para un residente | Paquete Amazon para Depto 302 |

### Jerarquía de residentes

Cada unidad tiene un **responsable de pago** (propietario o inquilino, vinculado a un `cliente_cobro` — el mismo registro que usa CobraYa para cobrar expensas) y, opcionalmente, **residentes vinculados** que no pagan pero viven en la unidad: familiares, mascotas o vehículos. Los vinculados tienen su propio nombre, documento y teléfono, y quedan asociados al responsable de pago de su unidad mediante el campo `vinculado_a`.

Esta jerarquía es la base de todo el módulo: determina quién recibe comunicados, quién puede generar códigos de visita, y quién puede tener su propia cuenta en el app de moradores.

---

## 🏢 La "administradora" y múltiples condominios

Una misma cuenta de PagosYa (un mismo `owner`) puede gestionar **más de un condominio** creando varias tiendas. Es el caso típico de una **administradora de condominios** que opera varios edificios.

- Las páginas del módulo (`/condominios/*`) muestran un **selector de condominio** en la parte superior cuando el dueño tiene más de una tienda; todos los datos (unidades, residentes, cobros, contabilidad) quedan aislados por `tienda_id`.
- La facturación y los límites del plan se aplican por tienda dentro de la suscripción; un cobrador/administrador con acceso a varias tiendas opera cada condominio de forma independiente sin mezclar datos.
- Para dar acceso a un empleado (ej. un portero o cobrador) solo en un condominio concreto, se vincula su perfil a esa tienda y se le otorgan los permisos específicos del módulo (ver [Seguridad y permisos](#-seguridad-y-permisos)).

> En KB: una tienda = un condominio. Una administradora con 3 edificios crea 3 tiendas bajo la misma cuenta y las administra desde el mismo login, con los datos siempre separados.

---

## 🖥️ Páginas del módulo (panel del administrador)

Todas viven bajo `/condominios/*` y requieren la feature `condominios`.

### `/condominios/residentes` — Residentes y unidades

Dos pestañas:

- **Residentes**: vista jerárquica — cada unidad muestra su responsable de pago y, expandible, sus vinculados (familiares/mascotas/vehículos). Acciones: nuevo registro, buscar, filtrar por unidad, **generar/copiar link del app** (botón 🔗), editar, excluir, ver detalle (modal con foto, parentesco y vinculados).
- **Unidades**: CRUD de `condo_units` — número, tipo (casa/departamento/local comercial/otro), torre/grupo, estado (activa/inactiva), notas.

**Roles y cobro**: los roles `propietario`/`inquilino` se vinculan a un `cliente_cobro` existente (o se crea uno) y marcan `es_responsable_pago`. Los roles `familiar`/`mascota`/`vehiculo`/`otro` no generan cobro propio — se registran con nombre, parentesco, documento, teléfono y foto, y quedan automáticamente vinculados al responsable de pago de la unidad.

**Link del app**: la página llama a la RPC `assign_condo_resident_portal_token` para generar/obtener el token del morador y arma el link `https://pagosya.com.bo/m/<token>`, que el administrador copia y comparte con el residente (por el medio que quiera). El límite de unidades se pre-valida con `getSubscriptionUsage` (la autoridad final es el trigger `enforce_condo_unit_limit`).

### `/condominios/comunicados` — Comunicados

- Título, mensaje, categoría (aviso/reunión/mantenimiento/emergencia/cobranza/general), prioridad (normal/importante/urgente, con badges de color).
- **Público-alvo** (`publico_tipo`): `todos` el condominio, `grupo` una torre/grupo específico, o `unidad` una unidad puntual. La base exige consistencia (no se puede marcar "todos" y a la vez un grupo).
- Al pasar un comunicado de **borrador** a **publicado**, la página invoca la edge function `condo-send-announcement-push`, que envía push a los residentes del público-alvo que tengan el app instalado.
- **Editar un comunicado ya publicado (corregir texto) no reenvía la notificación** — el push sólo se dispara en la transición borrador→publicado.

### `/condominios/reservas` — Reservas de áreas comunes

Dos pestañas:

- **Reservas**: filtros por estado/área/fecha/búsqueda. Acciones por reserva: **Aprobar / Rechazar** (con motivo) / **Cancelar**.
- **Áreas**: CRUD de `condo_common_areas` — nombre, descripción, capacidad, **tarifa**, reglas de uso, activo.

**Estados**: `solicitada → pendiente_pago → aprobada` o `rechazada/cancelada`.

**Cobro al aprobar**: si el área tiene tarifa > 0, aprobar crea (o reutiliza) un plan sintético **"Reserva de área"** (frecuencia `personalizada`, `es_recurrente = false`), lo vincula al cliente de la unidad, crea un `cobros` por el monto de la tarifa y deja la reserva en `pendiente_pago` con el `cobro_id` asociado. Si la tarifa es 0, se aprueba directo sin cobro.

**Detección de conflictos**: antes de confirmar, se consulta `condo_reservations` buscando solapamiento de horario (`hora_inicio < hFin` y `hora_fin > hInicio`) en estados `solicitada`/`aprobada`.

> 💡 Las reservas generan cobros **únicos** (`es_recurrente = false`), por lo que **no entran** en el ciclo automático de recordatorios de mensualidad (ver [Junção con WhatsApp CRM](#-junção-con-whatsapp-crm)).

### `/condominios/contabilidad` — Contabilidad del condominio

Tres pestañas:

- **Transacciones**: registro manual de ingresos y gastos por categoría (cuota, multa, reserva, otro ingreso; salario, servicios, mantenimiento, jardinería, seguridad, limpieza, otro gasto). Cards de totales Ingresos vs Gastos, filtros por tipo/mes/búsqueda. La columna `gasto_fijo_id` enlaza un gasto a su plantilla recurrente.
- **Gastos fijos**: plantillas de gastos recurrentes (ej. "Seguridad mensual") con día de vencimiento. Botón **"Generar del mes"** — crea las transacciones de gasto para todos los fijos activos que aún no se generaron en el mes corriente; es **idempotente** (no duplica gracias al `gasto_fijo_id`).
- **Reportes**: generador de reportes mensuales. Consolida `cobros` + `condo_transactions` del período, arma un `resumen_json` (emitido, recaudado, pendiente, vencido, balance) y construye un **HTML con gráficos SVG inline** (donut de gastos por categoría + barras de ingresos vs gastos), tabla de cuotas por unidad y detalle de transacciones. Se guarda en `condo_monthly_reports` como `borrador`, con preview en vivo. Botones **Descargar PDF** (`html2canvas` + `jsPDF`, paginado A4) y **Publicar** (pasa a `publicado` y queda visible para los moradores en su app/portal).

### `/condominios/visitas` — Control de visitas

- El **residente agenda la visita desde el portal/app** (nombre del visitante, documento, fecha, hora, motivo); el sistema genera un **QR real** (no decorativo) con el `qr_token` de la visita.
- En el panel, el portero **escanea el QR con la cámara** (`VisitQrScanner`): el **primer escaneo** marca la visita `pendiente → en_curso` (entrada), el **segundo escaneo** de la misma visita marca `en_curso → finalizada` (salida).
- También se puede ver el QR generado, o registrar/cambiar estado/eliminar manualmente sin cámara.
- Estados: `pendiente → en_curso → finalizada` o `cancelada`.

### `/condominios/encomendas` — Encomiendas y paquetes

- Registro: descripción, transportadora, **destinatario** (selección del residente de la unidad — importante en unidades con varias personas), fecha de recepción, foto del paquete (hasta 1 MB).
- El sistema genera automáticamente un **código de retiro de 4 dígitos** (`codigo_retiro`, por trigger `fn_generate_condo_package_codigo`) que el residente ve en su portal/app pero que **nunca se muestra al personal de portería**.
- **Entrega en dos pasos**: (1) el panel valida el código de 4 dígitos que dicta el morador con la RPC `check_condo_package_codigo`, que sólo responde "coincide sí/no" (nunca revela el código real) e incrementa `codigo_intentos`; (2) confirmada la coincidencia, se captura la **firma digital** en un canvas (mouse + touch) y la encomienda pasa a `entregada` con `firma_url`, `entregado_a` y `fecha_entrega`.
- Estados: `recibida → notificada → entregada`.

---

## 📲 App nativo "CobraYa" — el app del morador

El diferenciador principal del plan: un **app propio para los moradores**, con ícono y notificaciones distintas del app PagosYa del comerciante. Su objetivo central es reemplazar el recordatorio de pago por WhatsApp con **push gratuito**, y a la vez ofrecer las funciones condominiales (reservas, comunicados, visitas, encomiendas) como **valor agregado** que justifica instalarlo y mantenerlo — un app sólo de cobranza nadie lo instalaría.

> 📝 El nombre de visualización del app es **"CobraYa"** (package técnico histórico `com.pagosya.condominios`). Se genera con `capacitor.config.condominios.ts` + `build-condominios.ps1` (variable de build `VITE_APP_MODE=condominios_resident`), con su propio keystore, ícono azul y `google-services.condominios.json` dentro del mismo proyecto Firebase (`pagosya-13e24`).

### Cómo se instala y se parea

1. El administrador genera el **link personal** de un residente desde `/condominios/residentes`.
2. El residente abre el link. Si no tiene el app instalado, ve la misma información en el navegador (no pierde acceso mientras instala).
3. Al abrir el app por primera vez (`/m` — `CondoResidentEntryPage`), pega el link o el código que le pasó la administración. Si ya había una sesión guardada (`@capacitor/preferences`), entra directo sin volver a pedir el link.
4. Valida su identidad con **documento/CI o teléfono** (mismo mecanismo del portal web).
5. Una vez pareado, el app **recuerda la sesión** y registra el token de push del dispositivo.

### Qué puede hacer el residente en el app

Las mismas secciones del portal web, en una interfaz mobile-first con navegación por tarjetas (los ítems de condominio sólo aparecen si la unidad existe): **Expensas** (ver y pagar con QR, con badge de pendientes/vencidos), **Reservas**, **Comunicados** (con badge), **Contabilidad** (reportes publicados, con descarga PDF), **Visitas** (generar y compartir el QR de acceso), **Encomendas** (ver estado y código de retiro de 4 dígitos).

| Acción del residente | Cómo funciona |
|---|---|
| Pagar expensa / reserva | Genera el QR bancario vía `cobro-generate-qr`; hace polling cada 5 s hasta confirmar el pago (check verde). Puede descargar/compartir el QR. |
| Solicitar reserva | RPC `create_condo_reservation_by_portal_token`; mapea errores (`horario_ocupado`, `fecha_pasada`, `hora_invalida`). Si queda `pendiente_pago`, genera el cobro y el QR igual que una expensa. |
| Agendar visita | RPC `create_condo_visit_by_portal_token` devuelve un `qr_token` que se convierte en QR y se comparte con el visitante (`navigator.share`). |
| Ver encomienda | `get_condo_package_codigo_by_portal_token` revela el código de retiro de 4 dígitos de su paquete. |
| Ver reporte contable | `get_condo_report_by_portal_token` trae el HTML del reporte publicado, con botón de descarga PDF. |
| Ver comunicados | Solo lectura vía `get_condo_announcements_by_portal_token`. |

### Notificaciones push

| Evento | Cuándo se envía | Quién lo dispara |
|--------|-----------------|------------------|
| Recordatorio de pago de expensa | Antes del vencimiento, el día, y después de vencido — igual al ciclo de CobraYa, pero por push | `cobro-send-reminders` (cron, 4×/día) |
| Comunicado nuevo | Al publicarse (inmediato) | `condo-send-announcement-push` (on-demand) |

El **canal se configura por el administrador** en `/cobros/notificaciones`: WhatsApp, Push o Ambos. Si el residente no tiene el app instalado (sin token de push activo), el sistema **cae automáticamente a WhatsApp** — nunca se deja de avisar por falta del app.

> 🔋 **Importante para que el push llegue:** muchos Android chinos (Xiaomi, Huawei, Oppo, Vivo) matan las apps en segundo plano por defecto. El app muestra un `NotificationSetupCard` guiando al morador a desactivar la "optimización de batería" y activar el "inicio automático" para la app — sin ese paso, los push pueden no llegar cuando la app está cerrada.

### Cada morador puede tener su propia cuenta

A diferencia del portal web (un solo link compartido por unidad), el app permite que **cada persona de la casa tenga su propio login y su propio dispositivo registrado** — el titular y sus familiares pueden instalar el app cada uno en su celular, cada uno con su propio código de acceso y su propio historial de push, sin necesidad de compartir el documento del titular.

### Cómo se autentica el morador (dos capas de token)

El acceso del morador funciona con **tokens opacos de 256 bits** (64 caracteres hex, generados con `gen_random_bytes(32)`), sin contraseña ni cuenta `auth.users`:

| Token | Dónde vive | Para qué sirve |
|-------|-----------|----------------|
| `condo_residents.portal_token` | `condo_residents` | Login del app (`condo-resident-portal-access`) y registro del device token de push |
| `clientes_cobro.portal_token` ("unit_access_token") | `clientes_cobro` | Todas las RPC `*_by_portal_token` del portal/app y el portal web `/portal-cobro/:token` |

Al loguearse en el app, la edge function `condo-resident-portal-access` valida el token del residente + documento/teléfono, resuelve el responsable de pago (vía `vinculado_a` si es un familiar) y devuelve el `unit_access_token` (el token del `clientes_cobro` de la unidad), que a partir de ahí se usa para todas las consultas. Las RPC siempre validan el token en el servidor y acotan cada acción a los datos de esa unidad/residente.

---

## 🔗 Junção con WhatsApp CRM

El plan Condominios **incluye WhatsApp CRM completo** (bandeja compartida, chatbot, pipeline, envío en masa, plantillas, agenda de citas). Quien contrata Condominios ya está pagando por el CRM — nunca se contratan por separado. La unión entre el módulo condominial y el WhatsApp CRM se da en **tres puntos concretos**:

### 1. El número de WhatsApp (compartido por `tienda_id`)

El mismo número conectado en `whatsapp_instances` (API oficial Meta o Evolution) que la administración usa en la bandeja del CRM **es el número que dispara los recordatorios automáticos de expensas**. Un solo número, una sola conexión, dos usos.

### 2. La configuración central (`cobros_whatsapp_config`)

Una tabla por `tienda_id` guarda todo: el `canal_notificacion` (whatsapp/push/ambos), los templates de WhatsApp (antes/día/después) y los templates de push (título + cuerpo). La página `/cobros/notificaciones` (compartida con CobraYa) es la UI única para editar todo. El CRM y el motor de recordatorios leen y escriben la misma configuración.

### 3. El motor `cobro-send-reminders`

La edge function que produce el evento (recordatorio de pago) y lo entrega por el canal configurado. Extiende el ciclo CobraYa con dos adiciones específicas para Condominios:

- **Resolución de push por unidad**: si el cobro tiene `condo_unit_id`, busca los tokens activos en `condo_device_tokens` de los residentes de esa unidad (canal FCM `pagosya_condominios_reminders`). Si es un cliente CobraYa puro, usa `client_device_tokens`.
- **Filtro de recurrencia**: el ciclo automático sólo incluye cobros donde `planes_cobro.es_recurrente !== false`. Los cobros únicos de **reserva de área** quedan fuera del ciclo de recordatorios automáticos. (El envío manual de un cobro puntual sí ignora este filtro.)

**Decisión de canal y fallback obligatorio:**

```
canal = 'whatsapp'  → solo WhatsApp
canal = 'push'      → push; SI la unidad no tiene device token activo, cae a WhatsApp
canal = 'ambos'     → intenta los dos cuando estén disponibles
```

La pieza clave del fallback: `wantsWhatsapp = (canal !== 'push') || pushTokens.length === 0`. Es decir, aunque el canal esté en "Solo Push", si el residente no tiene el app, el recordatorio **igual se envía por WhatsApp**. Nunca se deja de avisar por falta del app.

**Anti-spam (solo WhatsApp):** 4 s entre mensajes, 12 mensajes por lote, pausa de 90 s entre lotes, tope diario por tienda (`max_por_dia`, default 50). El push no tiene rate-limiting (no hay riesgo de baneo).

**Dos proveedores de WhatsApp:** Evolution API (texto libre, aplica los templates editables de la tienda) y Meta Cloud API (requiere plantillas aprobadas: `pagosya_cobro_recordatorio`, `pagosya_cobro_vence_hoy`, `pagosya_cobro_vencido`; sin plantilla aprobada, el recordatorio se omite). Si el link del portal falta para un cliente, el recordatorio también se omite antes de enviar un link roto (de ahí el auto-llenado de `portal_token`, ver [Notas operativas](#-notas-operativas-y-gotchas)).

---

## 🔔 Configuración de notificaciones — `/cobros/notificaciones`

Página compartida con CobraYa base (reemplaza la antigua "Configuración de WhatsApp"; la ruta `/cobros/whatsapp` redirige aquí). Selector de canal:

| Opción | Comportamiento |
|--------|----------------|
| **Solo WhatsApp** | Todos los recordatorios van por WhatsApp (comportamiento clásico de CobraYa) |
| **Solo Push (app)** | Recordatorios por el app; si el residente no lo tiene instalado, cae a WhatsApp automáticamente |
| **Ambos** | Envía por los dos canales cuando estén disponibles |

Ambos canales tienen **templates editables** con variables y vista previa:

- **WhatsApp** (3 tabs: antes/día/después): variables `{{cliente}}`, `{{plan}}`, `{{monto}}`, `{{fecha}}`, `{{portal_link}}`, `{{tienda}}` y `{{mora_msg}}` (sólo vencido). Botón para resetear a defaults.
- **Push** (título + cuerpo separados por etapa, sin formato WhatsApp).

**Agendamiento:** días antes del vencimiento (default 3), enviar el día (bool), enviar después de vencido (bool) + días después (default 1), máximo por día (default 50).

**Estado del canal WhatsApp:** la página verifica la conexión (`whatsapp_instances.provider`) y qué plantillas Meta están aprobadas. Si faltan, el botón **"Crear plantillas"** llama a la edge function `whatsapp-meta` (`action: 'ensure_cobro_templates'`) y muestra el resultado por plantilla.

---

## 🏠 Sin lógica de caja/POS

CobraYa Condominios **no usa el módulo de caja registradora**. Al iniciar sesión, el usuario entra directamente en `/cobros` (que funciona como el dashboard del plan) — no hay pantalla de "abrir caja" ni bloqueo relacionado, ya que el plan no tiene punto de venta.

### Barra lateral organizada para el plan

El menú lateral de este plan tiene un orden propio (distinto de los demás planes de PagosYa), pensado para el uso diario de una administración de condominio:

1. **Cobros** (dashboard del plan)
2. **Gestión del condominio** — Residentes, Comunicados, Reservas, Contabilidad, Visitas, Encomiendas
3. **Administración** — Tiendas, Empleados
4. **WhatsApp CRM**
5. **Ayuda** — Guía de uso, Soporte

---

## 🔐 Seguridad y permisos

### Cargos personalizados

El administrador puede crear cargos a medida (ej. **"Portero"**) desde `/permissions` y otorgar acceso granular por módulo. Los seis permisos del módulo condominial son independientes entre sí:

| Permiso | ¿Qué habilita? |
|---------|-----------------|
| `condominios_residentes` | Ver/editar unidades y residentes |
| `condominios_comunicados` | Publicar comunicados |
| `condominios_reservas` | Gestionar reservas de áreas comunes |
| `condominios_contabilidad` | Ver/editar transacciones y generar reportes |
| `condominios_visitas` | Escanear QR y gestionar visitas |
| `condominios_encomendas` | Registrar y entregar encomiendas |

**Ejemplo típico:** un cargo "Portero" con sólo `condominios_visitas` y `condominios_encomendas` — ve únicamente esas dos secciones en su sidebar, sin acceso a residentes, comunicados, reservas ni contabilidad.

### Acceso del residente (portal y app)

- **Sin contraseña**: acceso por token opaco de 256 bits + validación de documento/CI o teléfono (mismo mecanismo del portal de CobraYa).
- Las RPC del portal/app siempre validan el token en el servidor (nunca confían en el usuario autenticado del navegador), y cada acción queda acotada a los datos de esa unidad/residente.
- El **código de retiro de encomiendas nunca se expone** al panel de administración — la RPC `check_condo_package_codigo` sólo responde "coincide sí/no"; el código real sólo lo ve el residente vía `get_condo_package_codigo_by_portal_token`.

### RLS (Row Level Security)

Todas las tablas del módulo tienen políticas RLS por `tienda_id` (dueño y empleados de esa tienda) más `service_role` para las Edge Functions del portal/app. Los registros de push (`condo_device_tokens`, `client_device_tokens`) **no** aceptan INSERT/UPDATE/DELETE directo de `anon`/`authenticated` — sólo se escriben vía RPC `SECURITY DEFINER` o `service_role`.

---

## 🗄️ Tablas de base de datos

| Tabla | Descripción |
|-------|------------|
| `condo_units` | Unidades del condominio (número, tipo, torre/grupo, estado) |
| `condo_residents` | Residentes por unidad — titulares y vinculados, con jerarquía `vinculado_a` y `portal_token` propio |
| `condo_announcements` | Comunicados (público-alvo, categoría, prioridad) |
| `condo_common_areas` | Áreas comunes reservables (capacidad, tarifa, reglas) |
| `condo_reservations` | Reservas de áreas comunes (estado, `cobro_id` asociado) |
| `condo_transactions` | Transacciones contables (ingresos/gastos, `gasto_fijo_id`) |
| `condo_fixed_expenses` | Plantillas de gastos fijos recurrentes |
| `condo_monthly_reports` | Reportes mensuales (borrador/publicado, HTML + resumen JSON) |
| `condo_visits` | Visitas registradas (con `qr_token` de acceso) |
| `condo_packages` | Encomiendas (destinatario, `codigo_retiro`, firma digital) |
| `condo_device_tokens` | Tokens de push del app nativo, por residente |
| `client_device_tokens` | Tokens de push de clientes CobraYa puros (paralela a la anterior) |
| `planes_cobro.es_recurrente` | `false` distingue cobros únicos (ej. reservas) de mensualidades reales |
| `cobros_whatsapp_config` | Canal de notificación (WhatsApp/Push/Ambos) y templates de ambos canales |

**Triggers relevantes:** `enforce_condo_unit_limit` (bloquea exceder unidades del plan), `fn_auto_set_condo_unit_id` (resuelve la unidad de un cobro por el cliente), `fn_generate_condo_package_codigo` (genera el código de 4 dígitos al crear encomienda), y `trg_clientes_cobro_portal_token` (todo cliente nuevo nace con `portal_token`).

---

## 🤖 Backend — funciones y automatización

### Edge Functions

| Función | Tipo | ¿Qué hace? |
|---------|------|-----------|
| `condo-resident-portal-access` | Auth (pública) | Valida `portal_token` + documento/teléfono del residente (titular o familiar) para el app nativo; devuelve el `unit_access_token` y los datos de la unidad |
| `condo-send-announcement-push` | On-demand | Envía push a los residentes del público-alvo al publicar un comunicado |
| `cobro-send-reminders` | Cron (4×/día) | Motor de recordatorios — resuelve canal por tienda, busca tokens de push, aplica el fallback a WhatsApp y excluye cobros no recurrentes |
| `cobro-generate-qr` | On-demand | Genera el QR bancario real (Baneco/BNB/Red Enlace) para pagar una expensa/reserva |

El push se envía vía `_shared/fcm.ts` (FCM v1, proyecto `pagosya-13e24`). Cuando FCM responde `UNREGISTERED` (app desinstalada/token inválido), el helper marca automáticamente `is_active = false` en la tabla de tokens — limpieza sin acción manual.

### RPCs `*_by_portal_token` (todas SECURITY DEFINER, validan el token del `clientes_cobro` de la unidad)

| RPC | Acción |
|-----|--------|
| `get_condo_unit_by_portal_token` | Datos de la unidad + cobros del morador |
| `get_condo_announcements_by_portal_token` | Comunicados visibles al morador (todos/grupo/unidad) |
| `get_condo_areas_by_portal_token` / `get_condo_reservations_by_portal_token` | Áreas activas / reservas del morador |
| `create_condo_reservation_by_portal_token` | Crear reserva (con validación de conflicto de horario) |
| `get_condo_accounting_by_portal_token` / `get_condo_report_by_portal_token` | Listado de reportes publicados / HTML de un reporte |
| `get_condo_visits_by_portal_token` / `create_condo_visit_by_portal_token` | Listar visitas / agendar visita (devuelve `qr_token`) |
| `get_condo_packages_by_portal_token` / `get_condo_package_codigo_by_portal_token` | Listar paquetes (sin código) / revelar código de retiro |
| `register_condo_device_token_by_resident_token` | Registra el token de push del dispositivo al parear el app |
| `check_condo_package_codigo` | Valida código de encomienda (sí/no) desde el panel del portero |

---

## 🧪 Notas operativas y gotchas

- **Precios/empleados desfasados en `get_plan_features`:** la función SQL `get_plan_features` (migration `20260712000001`) aún devuelve precios y conteos de empleados antiguos (Bs. 299/499/799/1099, 3/5/8/12 empleados) que no coinciden con los valores vigentes del frontend (`planPricing.ts` / `plansConfig.ts`: Bs. 449/699/999/1399, 3/5/10/15). El precio que se cobra en el checkout es el del frontend (correcto); pero cualquier validación server-side vía `get_plan_features` devolverá valores viejos. Pendiente regenerar la función SQL.
- **`portal_token` universal en `clientes_cobro`:** desde la migration `20260811000001`, todo cliente nuevo nace con `portal_token` (trigger) y los ~130 clientes legados sin token fueron retroactivos. Sin token, el botón de la plantilla Meta no identifica al cliente y el recordatorio se omite en vez de enviar un link roto.
- **Push en Android chinos:** sin desactivar la optimización de batería / activar el inicio automático, los push pueden no llegar con la app cerrada (Xiaomi/Huawei/Oppo/Vivo). El app lo guía, pero conviene anticiparlo en el onboarding del morador.
- **App Link (deep link HTTPS) no implementado todavía:** el pareo funciona 100% pegando el link manualmente en la pantalla `/m`. Falta el `assetlinks.json` + SHA-256 de la keystore para que el link `https://.../m/:token` abra el app directo. El `AndroidManifest.xml` del app principal no se modifica por esa misma razón.
- **Plan piloto legado:** existe un `CobraYa_Condominios_v1` (sin tier) con un tenant piloto activo, mantenido intocado. Los planes vigentes son los cuatro tiered + Corporativo.

---

## ❓ FAQ

**P: ¿CobraYa Condominios incluye todo lo de CobraYa base?**
R: Sí. Dashboard de cobros, clientes, planes, QR bancario sin comisión, portal del cliente, validación automática de pago, recibos y WhatsApp CRM funcionan exactamente igual — ver [32-cobraya-cobros-mensualizados.md](32-cobraya-cobros-mensualizados.md). Este plan solo agrega el módulo condominial encima.

**P: ¿Cuál es la diferencia entre CobraYa y CobraYa Condominios?**
R: Son planes distintos para públicos distintos. CobraYa es cobranza recurrente genérica (academias, gimnasios, colegios). CobraYa Condominios está dirigido a condominios/edificios: incluye todo lo de CobraYa y suma el módulo condominial (residentes, comunicados, reservas, contabilidad, visitas, encomendas) más el app del morador con push.

**P: ¿Un familiar necesita el documento del propietario para usar el app?**
R: No. Cada residente vinculado tiene su propio documento/teléfono registrado, su propio `portal_token` y su propio link de acceso — no depende de los datos del titular.

**P: ¿Qué pasa si un residente no instala el app?**
R: Sigue recibiendo los recordatorios y comunicados por WhatsApp normalmente. Si el canal está en "Solo Push" o "Ambos", el sistema cae a WhatsApp automáticamente cuando no hay push disponible.

**P: ¿El código de retiro de una encomienda se puede consultar desde el panel del portero?**
R: No, nunca. El panel solo puede preguntar "¿este código coincide?" y recibe sí/no — el código real solo lo ve el residente en su portal/app.

**P: ¿Se puede reservar un área sin pagar?**
R: Depende de la configuración del área — si la tarifa es cero, la reserva se confirma sin pago; si tiene tarifa, se genera un cobro con QR bancario que debe pagarse para confirmar. Ese cobro es único (no entra en los recordatorios automáticos de mensualidad).

**P: ¿El plan tiene caja registradora o POS?**
R: No. Es un plan 100% de cobranza y gestión condominial — no incluye punto de venta, productos ni inventario.

**P: ¿Una administradora con varios edificios necesita varias cuentas?**
R: No. Una sola cuenta (un `owner`) puede crear varias tiendas — una por condominio — y operarlas desde el mismo login con un selector, con los datos siempre separados por `tienda_id`.
