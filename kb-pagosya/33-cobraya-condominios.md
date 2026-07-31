---
title: "CobraYa Condominios"
version: 1.0
audiencia: "merchants, agents, support"
actualizado_en: 2026-07-11
---

CobraYa Condominios es el **plan especializado de PagosYa para administración de condominios, edificios y urbanizaciones**. Es una extensión de [CobraYa — Cobros Mensualizados](32-cobraya-cobros-mensualizados.md): incluye **todo** lo que trae CobraYa (cobranza recurrente de expensas, QR bancario sin comisión, portal del cliente, WhatsApp CRM) y agrega un **módulo completo de gestión condominial**: residentes, comunicados, reservas de áreas comunes, contabilidad, control de visitas y encomendas — más un **app Android nativo para los moradores** con notificaciones push gratuitas.

> 📄 La parte de cobranza (dashboard `/cobros`, clientes, planes, QR bancario, portal de pago, WhatsApp CRM) es **idéntica** a CobraYa base — ver [32-cobraya-cobros-mensualizados.md](32-cobraya-cobros-mensualizados.md). Este documento cubre **solo lo adicional** del módulo Condominios.

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

| Plan | Clientes (unidades) | Tiendas | Empleados | Precio |
|------|---------------------|---------|-----------|--------|
| **CobraYa Condominios** | Hasta 300 | 1 | Hasta 5 | A definir comercialmente (plan tipo enterprise) |

> El plan se activa manualmente por el equipo comercial — no está en el flujo de autoservicio de `/planes`. Incluye `monthly_billing` (CobraYa base) + `condominios` (módulo condominial) activados juntos; no incluye POS, productos ni tienda online.

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
| **Visita** | Registro de acceso de un tercero | "Juan Pérez visita Depto 302" |
| **Encomienda** | Paquete recibido en portería para un residente | Paquete Amazon para Depto 302 |

### Jerarquía de residentes

Cada unidad tiene un **responsable de pago** (propietario o inquilino, vinculado a un `cliente_cobro` — el mismo registro que usa CobraYa para cobrar expensas) y, opcionalmente, **residentes vinculados** que no pagan pero viven en la unidad: familiares, mascotas o vehículos. Los vinculados tienen su propio nombre, documento y teléfono, y quedan asociados al responsable de pago de su unidad.

Esta jerarquía es la base de todo el módulo: determina quién recibe comunicados, quién puede generar códigos de visita, y quién puede tener su propia cuenta en el app de moradores.

---

## 📱 Páginas del módulo (panel del administrador)

### `/condominios/residentes` — Residentes y unidades

- Vista agrupada: cada unidad muestra su responsable de pago y, expandible, sus vinculados (familiares/mascotas/vehículos)
- Alta de unidad: número, tipo (casa/departamento/local comercial/otro), torre/grupo, estado (activa/inactiva)
- Alta de residente: si es propietario/inquilino se vincula a un cliente de cobro existente (o se crea uno); si es familiar/mascota/vehículo se registran datos propios (nombre, parentesco, documento, teléfono, foto)
- **Generar link del app**: cada residente (incluyendo familiares) puede recibir su propio link personal para instalar y parear el app de moradores — sin necesidad de compartir el documento del titular

### `/condominios/comunicados` — Comunicados

- Título, mensaje, categoría (aviso/reunión/mantenimiento/emergencia/cobranza/general), prioridad (normal/importante/urgente)
- **Público-alvo**: todo el condominio, una torre/grupo específico, o una unidad puntual
- Al publicar (o cambiar de borrador a publicado), el sistema **envía push automáticamente** a los residentes del público-alvo que tengan el app instalado — sin pasos adicionales
- Editar un comunicado ya publicado (corregir texto) no reenvía la notificación

### `/condominios/reservas` — Reservas de áreas comunes

- Administración de áreas: nombre, descripción, capacidad, tarifa, reglas de uso
- Calendario de reservas con detección de conflictos de horario
- Si el área tiene tarifa, la reserva genera automáticamente un cobro con **QR bancario** para que el residente pague al confirmar
- Estas reservas se registran como cobros **de tipo único** (no recurrente) — no entran en el ciclo de recordatorios automáticos de mensualidad

### `/condominios/contabilidad` — Contabilidad del condominio

- **Transacciones**: registro manual de ingresos y gastos por categoría (salarios, servicios, mantenimiento, jardinería, seguridad, limpieza, cuotas, multas, reservas, otros)
- **Gastos fijos**: plantillas de gastos recurrentes (ej. seguridad mensual) con botón "Generar del mes" — idempotente, no duplica si ya se generó
- **Reporte mensual**: genera un reporte HTML con diseño profesional — logo de la tienda, KPIs (recaudado, gastos, balance, morosidad), gráfico donut de gastos por categoría, gráfico de barras ingresos vs gastos, tabla de cuotas por unidad y detalle de transacciones
- **Descarga en PDF** del reporte, para compartir con el directorio o publicarlo en el portal

### `/condominios/visitas` — Control de visitas

- El **residente agenda la visita desde el portal/app**: nombre del visitante, documento, fecha, hora, motivo
- El sistema genera un **código QR real** (no decorativo) que el residente comparte con su visita (WhatsApp, imagen)
- El portero **escanea el QR con la cámara** desde el panel — primer escaneo marca "entrada" (en curso), segundo escaneo de la misma visita marca "salida" (finalizada)
- También se puede registrar/gestionar manualmente desde el panel sin cámara

### `/condominios/encomendas` — Encomiendas y paquetes

- Registro de una encomienda: descripción, **destinatario** (selección del residente de la unidad — importante en unidades con varias personas), fecha de recepción
- El sistema genera automáticamente un **código de retiro de 4 dígitos**, visible solo para el residente destinatario en su portal/app — nunca se muestra al personal de portería
- Al retirar, el residente dicta el código al portero, quien lo valida en el panel (el sistema solo confirma "coincide sí/no", nunca revela el código real)
- Confirmada la coincidencia, se captura la **firma digital** de quien retira y la encomienda pasa a estado "entregada"

---

## 📲 App Android nativo — "PagosYa Condominios"

El diferenciador principal del plan: un **app propio para los moradores**, con ícono y notificaciones distintas del app PagosYa del comerciante, cuyo objetivo central es reemplazar el recordatorio de pago por WhatsApp con **push gratuito**.

### Cómo se instala y se parea

1. El administrador genera el **link personal** de un residente (titular o familiar) desde `/condominios/residentes`
2. El residente abre el link — si no tiene el app instalado, ve la misma información en el navegador (no pierde acceso mientras instala)
3. Dentro del app, valida su identidad con **documento/CI o teléfono** (mismo mecanismo del portal web)
4. Una vez pareado, el app **recuerda la sesión** — no vuelve a pedir el link ni los datos en las próximas aberturas

### Qué puede hacer el residente en el app

Las mismas secciones del portal web, en una interfaz mobile-first con navegación por pestañas: **Expensas** (ver y pagar con QR), **Reservas**, **Comunicados**, **Contabilidad** (reportes publicados), **Visitas** (generar y compartir QR de acceso), **Encomendas** (ver estado y código de retiro).

### Notificaciones push

| Evento | Cuándo se envía |
|--------|-----------------|
| Recordatorio de pago de expensa | Antes del vencimiento, el día, y después de vencido — igual al ciclo de CobraYa, pero por push |
| Comunicado nuevo | Al publicarse (inmediato) |

El **canal se configura por el administrador** en `/cobros/notificaciones`: WhatsApp, Push o Ambos. Si el residente no tiene el app instalado (sin token de push activo), el sistema **cae automáticamente a WhatsApp** — nunca se deja de avisar por falta del app.

### Cada morador puede tener su propia cuenta

A diferencia del portal web (un solo link compartido por unidad), el app permite que **cada persona de la casa tenga su propio login y su propio dispositivo registrado** — el titular y sus familiares pueden instalar el app cada uno en su celular, cada uno con su propio código de acceso y su propio historial de notificaciones push, sin necesidad de compartir el documento del titular.

---

## 🔔 Configuración de notificaciones — `/cobros/notificaciones`

Página compartida con CobraYa base (reemplaza la antigua "Configuración de WhatsApp"), con un selector de canal:

| Opción | Comportamiento |
|--------|----------------|
| **Solo WhatsApp** | Todos los recordatorios van por WhatsApp (comportamiento clásico de CobraYa) |
| **Solo Push** | Recordatorios por el app; si el residente no lo tiene instalado, cae a WhatsApp automáticamente |
| **Ambos** | Envía por los dos canales cuando estén disponibles |

Ambos canales tienen **templates editables** con variables (`{{cliente}}`, `{{plan}}`, `{{monto}}`, `{{fecha}}`, `{{tienda}}`, etc.) y vista previa en vivo — el push tiene título y cuerpo separados, sin formato de WhatsApp.

---

## 🏠 Sin lógica de caja/POS

CobraYa Condominios **no usa el módulo de caja registradora**. Al iniciar sesión, el usuario entra directamente en `/cobros` (que funciona como el dashboard del plan) — no hay pantalla de "abrir caja" ni bloqueo relacionado, ya que el plan no tiene punto de venta.

### Barra lateral organizada para el plan

El menú lateral de este plan tiene un orden propio (distinto de los demás planes de PagosYa), pensado para el uso diario de una administración de condominio:

1. **Cobros** (dashboard del plan)
2. **Gestión del condominio** — Residentes, Comunicados, Reservas, Contabilidad, Visitas, Encomendas
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

**Ejemplo típico:** un cargo "Portero" con solo `condominios_visitas` y `condominios_encomendas` activados — el portero ve únicamente esas dos secciones en su sidebar, sin acceso a residentes, comunicados, reservas ni contabilidad.

### Acceso del residente (portal y app)

- **Sin contraseña**: acceso por token único + validación de documento/CI o teléfono, mismo mecanismo de seguridad que el portal de CobraYa
- El código de retiro de encomiendas **nunca se expone** al panel de administración — solo se valida por coincidencia (sí/no)
- Las RPC del portal/app siempre validan el token en el servidor (nunca confían en el usuario autenticado del navegador), y cada acción queda acotada a los datos de esa unidad/residente

### RLS (Row Level Security)

Todas las tablas del módulo tienen políticas RLS por `tienda_id` (dueño y empleados de esa tienda) más `service_role` para las Edge Functions del portal/app.

---

## 📊 Tablas de base de datos

| Tabla | Descripción |
|-------|------------|
| `condo_units` | Unidades del condominio (número, tipo, torre, estado) |
| `condo_residents` | Residentes por unidad — titulares y vinculados (familiares/mascotas/vehículos), con jerarquía `vinculado_a` |
| `condo_announcements` | Comunicados (público-alvo, categoría, prioridad) |
| `condo_areas` | Áreas comunes reservables |
| `condo_reservations` | Reservas de áreas comunes |
| `condo_transactions` | Transacciones contables (ingresos/gastos) |
| `condo_fixed_expenses` | Plantillas de gastos fijos recurrentes |
| `condo_visits` | Visitas registradas (con `qr_token` de acceso) |
| `condo_packages` | Encomiendas (destinatario, código de retiro, firma digital) |
| `condo_device_tokens` | Tokens de push del app nativo, por residente |
| `planes_cobro.es_recurrente` | Distingue mensualidades reales de cobros únicos (ej. reservas) para el ciclo de recordatorios |
| `cobros_whatsapp_config` | Canal de notificación (WhatsApp/Push/Ambos) y templates de ambos canales |

---

## 🤖 Automatización (Edge Functions específicas del módulo)

| Función | ¿Qué hace? |
|---------|-----------|
| `condo-resident-portal-access` | Valida token + documento/teléfono de un residente (titular o familiar) para el app nativo |
| `condo-send-announcement-push` | Envía push a los residentes del público-alvo cuando se publica un comunicado |
| `register_condo_device_token_by_resident_token` (RPC) | Registra el token de push del dispositivo al parear el app |
| `check_condo_package_codigo` (RPC) | Valida el código de retiro de una encomienda sin exponerlo nunca al panel |

`cobro-send-reminders` (compartida con CobraYa base) fue extendida para resolver el canal por tienda (WhatsApp/Push/Ambos), buscar los tokens de push activos de la unidad, y **excluir automáticamente** los cobros de planes no recurrentes (como reservas) del ciclo de recordatorios.

---

## ❓ FAQ

**P: ¿CobraYa Condominios incluye todo lo de CobraYa base?**
R: Sí. Dashboard de cobros, clientes, planes, QR bancario sin comisión, portal del cliente y WhatsApp CRM funcionan exactamente igual — ver [32-cobraya-cobros-mensualizados.md](32-cobraya-cobros-mensualizados.md). Este plan solo agrega el módulo condominial encima.

**P: ¿Un familiar necesita el documento del propietario para usar el app?**
R: No. Cada residente vinculado tiene su propio documento/teléfono registrado y su propio link de acceso — no depende de los datos del titular.

**P: ¿Qué pasa si un residente no instala el app?**
R: Sigue recibiendo los recordatorios y comunicados por WhatsApp normalmente (si el canal está en "Push" o "Ambos", el sistema cae a WhatsApp automáticamente cuando no hay push disponible).

**P: ¿El código de retiro de una encomienda se puede consultar desde el panel del portero?**
R: No, nunca. El panel solo puede preguntar "¿este código coincide?" y recibe sí/no — el código real solo lo ve el residente en su portal/app.

**P: ¿Se puede reservar un área sin pagar?**
R: Depende de la configuración del área — si tiene tarifa en cero, la reserva se confirma sin pago; si tiene tarifa, se genera un cobro con QR bancario que debe pagarse para confirmar.

**P: ¿El plan tiene caja registradora o POS?**
R: No. Es un plan 100% de cobranza y gestión condominial — no incluye punto de venta, productos ni inventario.
