---
title: "CobraYa — Cobros Mensualizados"
version: 1.0
audiencia: "merchants, agents, support"
actualizado_en: 2026-06-12
---

CobraYa es el módulo de **cobranza recurrente automatizada** de PagosYa. Diseñado para negocios que necesitan gestionar, cobrar y hacer seguimiento de pagos periódicos: academias, gimnasios, colegios, universidades, guarderías, condominios, coworkings y membresías.

---

## 🎯 ¿Qué resuelve?

| Problema | Solución CobraYa |
|----------|-----------------|
| Cobrar manualmente cada mes a decenas o cientos de clientes | Generación automática de cobros por plan |
| Clientes que olvidan pagar | Recordatorios WhatsApp automáticos (3 días antes, el día, después) |
| Filas para pagar en efectivo | QR bancario + portal del cliente para autopago |
| Dueño que no sabe cuánto entra por mes | Dashboard con KPIs, gráficos y proyección |
| Clientes que piden comprobante | Recibo digital con logo de la tienda, imprimible |
| Error humano al registrar pagos | Auditoría de cada cambio de estado con motivo y responsable |

---

## 📦 Planes y precios

| Plan | Clientes | Mensual | Anual | Costo/cliente/mes |
|------|----------|---------|-------|-------------------|
| **CobraYa 300** ⭐ | Hasta 300 | Bs. 199 | Bs. 1.990 | Bs. 0.66 |
| **CobraYa 500** | Hasta 500 | Bs. 399 | Bs. 3.990 | Bs. 0.80 |
| **CobraYa 1000** | Hasta 1.000 | Bs. 699 | Bs. 6.990 | Bs. 0.70 |
| **Corporativo** | +1.000 | A negociar | — | — |

> 💡 **Ahorro vs pasarela (1%):** Para 300 clientes de Bs.150, CobraYa cuesta Bs.199/mes vs Bs.450/mes de pasarela = **56% menos**.

---

## 🧱 Estructura del módulo

### Entidades principales

| Entidad | ¿Qué es? | Ejemplo |
|---------|---------|---------|
| **Cliente de cobro** | Persona/entidad que recibe cobranzas | María López, alumna de crossfit |
| **Plan de cobro** | Template de cobranza recurrente | Membresía Básica — Bs.150/mes, vence el 5 |
| **Asignación** | Vínculo cliente ↔ plan | María está en Membresía Básica desde 01/06/2026 |
| **Cobro** | Cada cargo mensual generado | Junio 2026: Bs.150, vence 05/06/2026 |
| **Grupo** | Conjunto de clientes para organización | "5º A Mañana", "Torre A", "Membresía VIP" |

### Flujo de trabajo típico

```
1. Crear plan de cobro (monto, frecuencia, vencimiento)
2. Registrar clientes (nombre, teléfono, email)
3. Asignar clientes a planes (individual o por grupo)
4. El sistema genera cobros automáticamente cada mes
5. Clientes reciben recordatorios WhatsApp
6. Clientes pagan vía QR bancario o en persona
7. Dueño monitorea en dashboard y reportes
```

---

## 📱 Páginas del módulo

### `/cobros` — Dashboard

KPIs en tiempo real: emitido del mes, recaudado, tasa de cobranza, pendientes, vencidos, morosidad.

- **Gráfico de barras**: Emitido vs Recaudado por mes
- **Gráfico donut**: Distribución por estado (pagado, pendiente, vencido)
- **Top deudores**: Los 5 clientes con mayor saldo pendiente
- **Proyección del período**: Ingreso esperado según cobros activos
- **Barra de uso del plan**: Clientes X / límite Y con alerta de upgrade
- **Acciones rápidas**: Acceso directo a todas las secciones
- **Generar cobros / Actualizar vencidos**: Acciones manuales en menú ⚙️ (el cron las ejecuta automáticamente)

### `/cobros/clientes` — Gestión de clientes

- CRUD completo de clientes de cobro
- Filtros: búsqueda por nombre/email/teléfono/documento + filtro de portal (con/sin)
- **Paginación**: 10/25/50 por página con navegación completa
- **Import/Export CSV**: Carga masiva con validación de límite del plan
- **Portal del cliente**: Genera token para acceso seguro sin contraseña
- **Grupos**: Crear, editar, expandir grupos con miembros
- **Agregar a grupo**: Buscador con autocompletado (soporta 1000+ clientes)
- Clic en fila → Modal de cobro (POS-style con QR bancario)

### `/cobros/planes` — Configuración de planes

- CRUD de planes de cobro
- Campos: nombre, monto, frecuencia (mensual/trimestral/anual), día de cobro, tolerancia
- **Período**: fecha desde/hasta para planes con duración limitada (ej: año escolar)
- **Mora**: tipo (fijo/porcentaje), valor, días de gracia
- **Matrícula**: monto único al primer mes
- **Prorrateo**: calcula días restantes si el cliente entra a mitad de mes

### `/cobros/asignaciones` — Vínculos cliente-plan

- Asignar clientes a planes (individual o **por grupo**)
- Vista previa de miembros del grupo antes de asignar
- Fecha de inicio personalizable
- Monto personalizado por cliente (descuentos, becas)
- Desvincular con confirmación

### `/cobros/pendientes` — Cobros activos

**Solo muestra cobros accionables:** pendiente, vencido, parcial.

- Filtro rápido por mes (últimos 12 meses) + rango de fechas + búsqueda
- **Acciones por cobro:**
  - 💚 **Pagar** → Modal POS con selección de cobros, efectivo/transferencia/QR
  - 🔔 **Recordatorio** → Envía mensaje WhatsApp inmediato
  - 🔴 **Vencer** → Modal con motivo + contraseña (auditado)
  - ✕ **Anular** → Modal con motivo + contraseña (auditado)
- **Nuevo cobro manual**: Individual o por grupo, para cargos puntuales

### `/cobros/historial` — Historial completo

**Todos los cobros**, incluyendo pagados y cancelados.

- Filtros siempre visibles: pills de estado + calendario + búsqueda + cliente + plan
- Columnas: cliente, plan, monto, estado, emisión, vencimiento, **pagado**, **fecha pago**, recibo, acción
- Mismas acciones que pendientes (pagar, recordatorio, vencer, anular)
- Exportar CSV con todos los campos
- Recibo digital en modal con iframe (imprimir, compartir, descargar PNG)

### `/cobros/reportes` — Reportes de ingresos

- **4 KPIs**: Recaudado, Pendiente, Vencido, Cancelado/Anulado
- **Gráfico de líneas**: Ingresos últimos 30 días (emitido vs pagado)
- **Tabla detallada**: Nº cobro, monto, estado, emisión, vence, pago, **notas/auditoría**
- Las notas de anulación/vencimiento muestran quién, cuándo y por qué

### `/cobros/whatsapp` — Configuración de recordatorios

- **Editor de templates** con variables: `{{cliente}}`, `{{plan}}`, `{{monto}}`, `{{fecha}}`, `{{portal_link}}`, `{{mora_msg}}`, `{{tienda}}`
- 3 tipos de mensaje: antes del vencimiento, día del vencimiento, después de vencido
- **Vista previa en vivo** con datos de ejemplo
- Frecuencia configurable: días antes, enviar el día, enviar después
- Límite diario de mensajes por tienda (anti-spam)
- Botón restaurar a template default

### `/portal-cobro/:token` — Portal del cliente

Acceso público sin contraseña para que los clientes vean y paguen sus cobros.

- **Tela 1**: Validación con documento/CI o teléfono
- **Tela 2**: KPIs personales + timeline mensual + lista de cobros
- Clic en cobro pendiente/vencido → QR bancario para pagar
- Recibo digital disponible en cobros pagados
- Logo de la tienda + logo PagosYa en header
- Fully responsive mobile-first

---

## 🤖 Automatización (Edge Functions)

| Función | ¿Qué hace? | Frecuencia |
|---------|-----------|-----------|
| `generate-monthly-cobros` | Genera cobros para todas las asignaciones activas | Diario 2 AM |
| `update-vencidos` | Marca como vencido cobros con fecha pasada + calcula mora | Diario 3 AM |
| `cobro-send-reminders` | Envía recordatorios WhatsApp con rate-limiting | 4×/día (8 AM, 12 PM, 4 PM, 8 PM) |
| `cobro-generate-qr` | Genera QR bancario real vía Baneco/BNB/Red Enlace | On-demand |
| `cobro-generate-receipt` | Genera recibo HTML con logo de tienda | On-demand |
| `customer-portal-access` | Valida token + documento/teléfono para portal cliente | On-demand |

### Anti-spam en recordatorios

- 4 segundos entre cada mensaje
- 12 mensajes por lote, pausa de 90 segundos entre lotes
- Máximo 80 mensajes por ejecución (~5 msg/min promedio)
- 4 ejecuciones diarias = hasta 320 recordatorios/día
- Meta/WhatsApp no detecta como spam a este ritmo

---

## 🔐 Seguridad y permisos

### Permisos de empleado

| Permiso | Admin | Gerente | Cajero |
|---------|-------|---------|--------|
| `cobros_mensualizados` | ✅ | ❌ | ❌ |
| `cobros_anular` | ✅ | ❌ | ❌ |
| `cobros_vencer` | ✅ | ❌ | ❌ |
| `cobros_crear_manual` | ✅ | ❌ | ❌ |
| `cobros_ver_reportes` | ✅ | ❌ | ❌ |

### Acciones sensibles (anular/vencer)

Requieren:
1. **Motivo** obligatorio (textarea)
2. **Contraseña** del usuario (reautenticación)
3. Se registra en `cobros_audit_log` con trigger automático
4. La razón queda en `cobros.notas` como `[Anulado] motivo` o `[Vencido] motivo`

### RLS (Row Level Security)

Todas las tablas del módulo tienen políticas RLS por `tienda_id`. Service role tiene acceso total para las Edge Functions.

---

## 📊 Tablas de base de datos

| Tabla | Descripción |
|-------|------------|
| `clientes_cobro` | Clientes del módulo (nombre, email, tel, doc, portal_token) |
| `planes_cobro` | Planes de cobro (monto, frecuencia, mora, matrícula, prorrateo) |
| `cliente_plan_cobro` | Asignaciones cliente-plan (fecha_inicio, monto_personalizado) |
| `cobros` | Cada cobro generado (estado, monto, fechas, referencia_pago) |
| `grupos_cobro` | Grupos de clientes |
| `cliente_grupo_cobro` | Membresía de clientes en grupos |
| `cobros_audit_log` | Auditoría de cambios de estado (trigger automático) |
| `cobros_whatsapp_config` | Configuración de templates y frecuencia por tienda |

---

## 🚫 Límites del plan

- Al alcanzar el límite de clientes, el botón "Nuevo cliente" abre un **modal de upgrade** con los planes disponibles
- El **import CSV** se detiene al llegar al límite y también abre el modal
- El dashboard muestra una **barra de progreso** con colores (azul <70%, ámbar 70-90%, rojo >90%)
- Botón **"Actualizar plan"** visible a partir del 70%

---

## 💳 Integración bancaria — Pagos QR sin comisión

CobraYa se integra directamente con los **3 bancos principales de Bolivia** para generar QR de pago reales. Esto es un diferenciador único en el mercado boliviano.

### 🏦 Bancos integrados

| Banco | Código | Método QR |
|-------|--------|-----------|
| **Banco Económico (Baneco)** | `baneco` | QR Simple |
| **BNB** | `bnb` | QR BNB |
| **Red Enlace** | `redenlace` | QR Red Enlace |

### ⚡ Cómo funciona

1. El dueño **conecta su cuenta bancaria** en el panel de integraciones
2. Cuando un cliente quiere pagar, el sistema **genera un QR real** del banco activo
3. El cliente **escanea con su app bancaria** y paga en segundos
4. El sistema hace **polling automático** cada 5 segundos para verificar el pago
5. Al confirmar, el cobro se marca como **pagado automáticamente** y se registra en `sales_unified`

### 🆓 Cero comisión — Nuestro mayor diferencial

**PagosYa NO cobra comisión por transacción.** Esta es una ventaja competitiva enorme frente a las pasarelas de pago tradicionales:

| | PagosYa CobraYa | Pasarela de pago típica |
|---|----------------|------------------------|
| Comisión por pago | **0%** | 1% – 5% |
| Costo mensual | Plano fijo desde Bs.199 | Variable según volumen |
| 300 clientes × Bs.150 | **Bs.199/mes total** | Bs.450/mes solo en comisiones |
| 1.000 clientes × Bs.150 | **Bs.699/mes total** | Bs.1.500/mes solo en comisiones |

> 💡 **Somos posiblemente el único sistema en Bolivia que ofrece cobranza recurrente + QR bancario integrado + cero comisión.** El dueño paga una tarifa plana mensual y se olvida de porcentajes por transacción.

### Registro unificado de pagos

Todos los pagos — por QR, efectivo o transferencia — se registran en la tabla `sales_unified` con `sale_channel = 'cobro_mensualizado'`. Esto significa que:

- Aparecen en el dashboard de ventas general
- Se integran en los reportes financieros
- Son trazables y auditables en un solo lugar
- Compatibles con el sistema de facturación SIAT

### Seguridad en los pagos QR

- El QR se genera vía Edge Function con **service_role key**
- **Polling** verifica el estado del pago cada 5 segundos
- Al confirmar, el cobro se marca automáticamente — sin intervención manual
- **Anti-duplicación**: cada cobro se verifica contra `cliente_plan_id` + mes/año para no generar doble cargo

---

## 🔗 Portal del cliente — Página exclusiva de autogestión

**Cada cliente de CobraYa tiene su propio portal de pagos personalizado.** Es una página web accesible sin contraseña, protegida por un token único de 256 bits + validación de identidad.

### 🎯 ¿Qué puede hacer el cliente en su portal?

| Acción | Descripción |
|--------|------------|
| 📊 **Ver su estado** | KPIs personales: total pendiente, vencido, pagado |
| 🗓️ **Timeline mensual** | Visualizar mes a mes qué pagó y qué debe |
| 📱 **Pagar con QR** | Un clic sobre el cobro → QR del banco → escanea y paga |
| 🧾 **Descargar recibos** | Cada pago genera un recibo digital disponible 24/7 |
| 🔒 **Acceso seguro** | Sin contraseña — token único + validación CI o teléfono |

### 🔐 ¿Cómo accede el cliente?

1. El dueño genera un **link único** desde `/cobros/clientes` (botón 📋)
2. El cliente recibe el link por WhatsApp: `https://pagosya.com/portal-cobro/<token>`
3. Ingresa su **documento/CI** o **teléfono** para validar su identidad
4. Accede a su panel personal con todos sus cobros

### 🎨 Personalización del portal

- **Logo de la tienda**: se muestra el logo que el dueño subió en su perfil
- **Nombre de la tienda**: visible en todo el portal
- **Colores y estilo**: diseño profesional con branding de la tienda
- **Sin menciones a PagosYa**: el cliente ve solo el nombre y logo de la tienda

### 📱 Experiencia mobile-first

El portal está diseñado 100% responsive para celular. El cliente puede:

- Entrar desde el link de WhatsApp en su teléfono
- Ver sus cobros en una interfaz optimizada
- Tocar un cobro → generar QR → pagar con su app bancaria
- Descargar o compartir el recibo al instante

> 💡 **Cada cliente tiene su propia URL personal.** Esto elimina la fricción de "¿cómo pago?" — el cliente recibe el link, toca y paga. Sin apps, sin registros, sin contraseñas.

---

## 🎓 Onboarding rápido

1. **Crear planes de cobro** → `/cobros/planes`
2. **Registrar clientes** → `/cobros/clientes` (o importar CSV)
3. **Asignar clientes a planes** → `/cobros/asignaciones`
4. **Generar cobros del mes** → Dashboard → ⚙️ (o esperar al cron de las 2 AM)
5. **Configurar WhatsApp** → `/cobros/whatsapp` (personalizar mensajes)
6. **Compartir portal** → Copiar link desde `/cobros/clientes` para cada cliente

---

## 💬 WhatsApp CRM — Incluido sin costo adicional

**Todos los planes CobraYa incluyen WhatsApp CRM completo** como parte del paquete. Esto permite que la tienda no solo automatice la cobranza, sino que también gestione toda la comunicación con sus clientes en un solo lugar.

> 📄 Documentación completa: [22-whatsapp-crm.md](22-whatsapp-crm.md)

### ¿Por qué viene incluido?

La cobranza recurrente depende de la comunicación efectiva con los clientes. Los recordatorios de pago, las respuestas a consultas sobre saldos, y la gestión de reclamos son parte natural del ciclo de cobranza. WhatsApp CRM y CobraYa funcionan como un sistema integrado:

- **Recordatorios automáticos** → CobraYa dispara el mensaje vía WhatsApp CRM
- **Consultas de clientes** → "¿Cuánto debo?" → El dueño responde desde el chat unificado
- **Portal de pago** → El link del portal se envía automáticamente en cada recordatorio

### Funcionalidades del WhatsApp CRM incluidas

| # | Módulo | Descripción breve |
|---|--------|------------------|
| 1 | 💬 **Chat en tiempo real** | Bandeja compartida donde toda la equipe ve y responde mensajes de un mismo número |
| 2 | 🏷️ **Etiquetas y filtros** | Organizar contactos con 10 colores (VIP, pendiente, lead, etc.) |
| 3 | 🗂️ **Pipeline Kanban** | Visualizar en qué etapa del funil de ventas está cada contacto |
| 4 | 👤 **CRM de contactos** | Datos completos: empresa, cargo, email, ciudad, productos de interés |
| 5 | 📤 **Envío en masa** | Hasta 200 msg/día con delay anti-ban (8-45s) y pausas de 3 min cada 10 |
| 6 | ⚡ **Respuestas rápidas** | Biblioteca de mensajes con atajos `/comando` y 12 variables |
| 7 | 📋 **Templates con variables** | Mensajes profesionales que se llenan con datos del cliente automáticamente |
| 8 | 📅 **Agendamiento** | Programar mensajes con fecha/hora y recorrência (diaria, semanal, mensual) |
| 9 | 🤖 **Chatbot con IA** | Respuestas automáticas 24/7 con Google Gemini o ChatGPT |
| 10 | 🎨 **Campañas con IA** | Generar imágenes + copy promocional con IA |
| 11 | 📥 **Importación CSV** | Cargar contactos en segundos desde archivo |
| 12 | 📊 **Métricas** | KPIs en tiempo real: mensajes/día, ranking de atendentes, tasa de lectura |
| 13 | 🔍 **Histórico y exportación** | Búsqueda global + exportar en CSV o TXT |
| 14 | ⭐ **CSAT / NPS** | Encuesta de satisfacción 1-5★ con Net Promoter Score automático |

### Anti-spam / Anti-ban integrado

El WhatsApp CRM incluye protección contra bloqueos de Meta con:

- Distribución asimétrica de delays (simula comportamiento humano)
- Pausa de 3 minutos cada 10 mensajes
- Límite seguro de 200 mensajes/día
- Jobs que sobreviven al recargar la página

### Integración con CobraYa

| Flujo | Cómo funciona |
|-------|--------------|
| Recordatorio de pago | CobraYa → WhatsApp CRM → mensaje al cliente |
| Cliente responde "¿cuánto debo?" | WhatsApp CRM → dueño ve el chat → responde con datos de CobraYa |
| Cliente pide el link del portal | Dueño envía `/portal` (respuesta rápida) con el link |
| Campaña de nuevo ciclo | Dueño crea promo con IA → envía en masa a todos los clientes del grupo |

### Providers de IA incluidos

- **Google Gemini**: `gemini-2.0-flash` (default)
- **OpenAI**: `gpt-4o-mini` (alternativa)
- Configuración unificada entre Chatbot, Campañas y Templates

---

## ❓ FAQ

**P: ¿Puedo crear cobros manuales sin asignar un plan?**
R: Sí. En `/cobros/pendientes` → "Nuevo cobro". Son cobros **puntuales** (no se repiten).

**P: ¿Qué pasa si un cliente tiene 2 planes asignados?**
R: Es válido. Un alumno puede tener "Membresía Básica" + "Taller de Yoga". El sistema genera cobros separados para cada plan.

**P: ¿Cómo funciona la mora?**
R: Al marcar un cobro como vencido (manual o automático), el sistema calcula la mora según la configuración del plan: monto fijo o porcentaje sobre el valor original.

**P: ¿Los recordatorios WhatsApp son obligatorios?**
R: No. Se pueden desactivar por tienda en `/cobros/whatsapp`, o por cliente desmarcando "notificaciones activas".

**P: ¿El portal del cliente es seguro sin contraseña?**
R: Sí. Usa un token hexadecimal de 256 bits generado con `gen_random_bytes(32)`. El acceso requiere además validar documento/CI o teléfono del cliente.

**P: ¿Puedo cambiar de plan CobraYa en cualquier momento?**
R: Sí. Desde el dashboard, al llegar al 70% del límite aparece el botón "Actualizar plan" que lleva a `/planes`.
