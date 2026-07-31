---
title: "Nia — Asistente IA por WhatsApp"
version: 1.0
audiencia: "merchants, agents, support"
actualizado_en: 2026-07-28
---

**Nia** es el asistente personal con inteligencia artificial de PagosYa. Funciona **enteramente por WhatsApp**: el usuario escribe, manda un audio o una foto de recibo, y Nia registra gastos, crea recordatorios y genera cobros — conversando, sin abrir la app.

---

## 🎯 ¿Qué resuelve?

| Problema | Solución Nia |
|----------|---------------|
| El comerciante no anota sus gastos porque abrir una app le da pereza | Manda un audio de 5 segundos mientras camina y queda registrado |
| Olvida pagar el alquiler, llamar al contador, revisar stock | Recordatorios por WhatsApp, incluso recurrentes |
| No sabe cuánto gastó este mes | Pregunta "¿cuánto gasté?" y recibe el resumen al instante |
| Cobrar a un cliente exige entrar al panel, generar QR, mandarlo | Dice "cobrale 100 Bs a María" y recibe el link listo para reenviar |
| No se entera cuando le pagan | Nia avisa apenas el pago entra |
| Guarda recibos de papel que se borran | Manda una foto y el gasto queda registrado |

---

## 📦 Plans y precios

Nia **no es un plan nuevo**: es un **add-on** que se suma a la suscripción que el comerciante ya tiene (EmprendeYa, ExpandeYa, ConquistaYa, CobraYa, etc.). El plan principal no cambia.

| Plan | Precio | Interacciones/mes | Incluye |
|--------|--------|-------------------|---------|
| **Nia Básico** | Bs. 0 | 50 | Gastos, recordatorios, resúmenes |
| **Nia Plus** | Bs. 29/mes | 300 | Todo lo anterior |
| **Nia Pro** | Bs. 49/mes | 300 | Todo + **cobro por WhatsApp** con confirmación automática |

### Créditos adicionales

El sistema de créditos de **Bs. 20** ya existente gana una cuarta opción de aplicación, junto a las tres actuales:

| Aplicación | Qué entrega |
|------------|-------------|
| Aumentar límite de ventas | +Bs. 5.000 permanentes |
| Combo de expansión | +1 tienda +1 empleado por 30 días |
| Facturas SIAT | +50 facturas |
| 🆕 **Interacciones con Nia** | **+150 interacciones** |

> Las interacciones compradas con créditos **no vencen**: se usan solo cuando se agotan las del plan.

---

## 💬 ¿Qué puede hacer?

### 1. Registro financiero

El usuario cuenta el gasto como se le ocurra. Nia extrae monto, categoría y descripción.

```
"gasté 150 en el almuerzo"
"pagué 320 de luz"
"recibí 2000 de la venta"
```

Respuesta:

```
🔴 Gasto registrado

💰  Bs 150,00
🏷️  comida
```

**Regla de seguridad:** si el monto no está claro, Nia **no registra** y pregunta. Es preferible pedir de nuevo que guardar un dato equivocado que el usuario verá después en su panel.

### 2. Recordatorios

```
"recordame mañana a las 15:00 llamar al doctor"
"recordame todos los lunes revisar el stock"
"¿qué recordatorios tengo?"
```

- Puntuales o **recurrentes** (diario, semanal, mensual)
- Se disparan con precisión de **5 minutos**
- Llegan por plantilla aprobada de WhatsApp, incluso fuera de la ventana de 24h
- Se editan o cancelan respondiendo al mensaje o desde el panel (título, fecha/hora, recurrencia, notas)

### 3. Cobro por WhatsApp *(solo Nia Pro)*

```
"cobrale 175 Bs a Ana Quispe por el servicio de julio"
```

Respuesta:

```
💳 Cobro creado

👤  Ana Quispe
💰  Bs 175,00
📝  Servicio de julio
━━━━━━━━━━━━━━
https://www.pagosya.com.bo/pay/bbe9eaa6-...

Reenvía este link a quien va a pagar.
✅ Te aviso apenas entre el pago.
```

**Por qué el link va al comerciante y no al cliente:** mandar un cobro a alguien que nunca escribió al número sería mensaje frío sin consentimiento — el patrón que Meta penaliza. Además, el comerciante casi siempre quiere mandar el link con su propio contexto. Reenviar es un gesto que ya hacía igual.

Cuando el cliente paga, Nia avisa automáticamente:

```
Pago recibido.

De: Ana Quispe
Monto: Bs 175,00
Concepto: Servicio de julio
```

---

## 🎙️ Audio y foto

| Entrada | Cómo funciona |
|---------|---------------|
| **Texto** | Directo |
| **Audio** | Se transcribe y entra al mismo flujo que un mensaje escrito |
| **Foto de recibo** | Se lee el monto y el comercio, y se convierte en gasto |

**El OCR no adivina.** Si el monto total no es legible, Nia responde pidiendo otra foto en lugar de registrar un número inventado.

Audio y foto **cuestan más** que texto y consumen más del paquete mensual:

| Tipo | Consumo |
|------|---------|
| Comando del menú (AYUDA, SALIR, idioma) | **0** |
| Mensaje de texto procesado por IA | 1 |
| Audio | 2 |
| Foto | 3 |
| Recordatorio enviado | 2 |

> Los comandos del menú son gratuitos a propósito: es por ahí que el usuario descubre cómo comprar créditos cuando llega al límite.

**Rajadas de mensajes:** si el usuario manda varios audios seguidos (típico de quien estuvo sin internet y acumuló), Nia los procesa **todos**, no solo el último — cada uno puede ser un gasto distinto.

---

## 🔗 Cómo se activa

1. El usuario entra a su cuenta PagosYa → menú **Nia**
2. Toca **"Generar código y conectar WhatsApp"** → aparece un código de 6 caracteres
3. Toca **"Abrir WhatsApp y enviar el código"** → se abre la conversación con Nia **con el código ya escrito**; solo hay que tocar enviar
4. Listo: la pantalla detecta la vinculación sola y pasa al panel

El código vence en 15 minutos. Si WhatsApp no se abre (por ejemplo, una computadora sin WhatsApp Web), la misma pantalla muestra el número de Nia y el código para copiar. En ese caso hay que enviar **solo el código** — sin «hola» ni «código» adelante, o no se reconoce como vinculación.

**Por qué un código y no solo el teléfono del registro:** el código prueba dos cosas al mismo tiempo — que la persona controla ese número *y* que tiene acceso a la cuenta. Sin eso, cualquiera podría registrar el teléfono de otro y recibir sus datos financieros.

Mientras no esté vinculado, Nia solo responde el onboarding: no accede a ningún dato.

### Desvincular y cambiar de número

En **Nia → Configuración → WhatsApp vinculado** hay un botón **Desvincular**. Nia deja de responder en ese número, y no se borra nada: movimientos, recordatorios, cobros, el consumo del mes y el plan quedan guardados.

| Después de desvincular | Qué pasa |
|---|---|
| Vincular **el mismo número** | El historial reaparece completo |
| Vincular **otro celular** | Nia empieza de cero: el historial queda guardado en la vinculación anterior pero ya no se muestra, y los recordatorios agendados no se trasladan al número nuevo |

Un recordatorio agendado antes de desvincular **no se entrega**: el número puede ya no ser de la misma persona, y el título de un recordatorio es contenido personal.

---

## 📱 Comandos

| Comando | Efecto |
|---------|--------|
| `AYUDA` / `AJUDA` / `MENU` / `?` | Menú de opciones |
| `1` `2` `3` `4` | Ejemplos de cada función |
| `SALIR` / `BAJA` / `STOP` | Deja de recibir mensajes |
| `VOLVER` / `ALTA` / `START` | Reactiva |
| `PORTUGUES` / `ESPAÑOL` | Cambia el idioma |

> `CANCELAR` **no** apaga el asistente — se reserva para cancelar un recordatorio.

---

## 🖥️ Panel `/asistente`

| Pestaña | Contenido |
|---------|-----------|
| **Resumen** | Gastos, ingresos, saldo e interacciones del mes + gráfico de 30 días |
| **Finanzas** | Gastos por categoría (con opción de unificar categorías) + tabla de movimientos, editables y eliminables |
| **Agenda** | Calendario mensual + próximos recordatorios, editables y cancelables |
| **Cobros** | Cobros generados y su estado |
| **Consumo** | Medidor de interacciones, saldo de créditos y CTA de compra |

El panel se actualiza **en tiempo real**: lo que se registra por WhatsApp aparece sin necesidad de refrescar la página. También permite **pausar** el asistente (botón Activo/Pausado) sin desvincular el número.

---

## 🌎 Idiomas

Nia habla **español y portugués**. El idioma se infiere del código de país en el primer contacto (+55 y +351 → portugués; el resto → español) y el usuario puede cambiarlo cuando quiera.

El **huso horario** también se infiere del país. Esto importa: "recordame mañana a las 12h" solo tiene sentido en la hora de quien habla. Un usuario boliviano y uno brasileño tienen 1 hora de diferencia.

---

## ⚙️ Características técnicas

### Arquitectura

```
WhatsApp (Meta Cloud API)
      ↓  firma HMAC validada
whatsapp-meta-webhook  (edge function — enrutador central)
      ↓  secreto compartido
n8n  (workflow dedicado)
      ↓  RPCs SECURITY DEFINER
Supabase (Postgres)
```

### Componentes

| Componente | Función |
|------------|---------|
| `whatsapp-meta-webhook` | Valida la firma de Meta y enruta al asistente |
| Workflow n8n | Clasificación, IA, respuestas |
| `ai-assistant-media` | Transcribe audio (Whisper) y lee recibos (visión) |
| `ai-assistant-reminder-sender` | Consume la cola de recordatorios (cron cada 5 min) |
| `ai-assistant-payment-notify` | Avisa cuando un cobro se paga |

### Datos

| Tabla | Qué guarda |
|-------|-----------|
| `ai_assistant_users` | Identidad: número ↔ cuenta, idioma, huso, estado |
| `ai_assistant_messages` | Historial y base del contador de consumo |
| `ai_assistant_transactions` | Gastos e ingresos |
| `ai_assistant_reminders` | Recordatorios y su recurrencia |
| `ai_assistant_charges` | Cobros generados |

Todas con **RLS**: cada usuario solo ve lo suyo.

### Modelo de IA

Modelo económico (`gpt-4.1-mini`) con salida estructurada en JSON. Transcripción con Whisper, orientada con vocabulario del dominio para no confundir palabras parecidas.

### Seguridad

- **Firma HMAC** de Meta validada antes de cualquier procesamiento
- **Secreto compartido** entre el webhook y n8n
- Nia **nunca** entra al flujo del WhatsApp CRM comercial — está aislado por número
- Los accesos a datos pasan por funciones que resuelven el dueño internamente, nunca por parámetro

---

## 🚧 Límites actuales

| Límite | Detalle |
|--------|---------|
| Precisión del recordatorio | ±5 minutos (el cron corre cada 5) |
| Moneda | Solo bolivianos (Bs). Un usuario que diga "reales" recibe un pedido de aclaración |
| Cobro | Exige **Nia Pro** y banco vinculado a la cuenta |
| Video y documentos | No se procesan (sí audio e imagen) |
| Un número por cuenta | Cada número se vincula a una sola cuenta |

---

## ❓ Preguntas frecuentes

**¿Necesito cambiar de plan para usar Nia?**
No. Es un add-on: el plan actual sigue igual y Nia se suma encima.

**¿Qué pasa si llego al límite de interacciones?**
Nia avisa y deja de procesar mensajes de IA hasta el mes siguiente. Los comandos del menú siguen funcionando, y se pueden comprar créditos para continuar.

**¿Mis datos financieros son privados?**
Sí. Solo se accede a los datos de la cuenta vinculada a ese número, y la vinculación exige un código generado desde adentro de la cuenta.

**¿Puedo pausar sin perder el historial?**
Sí, con el botón Activo/Pausado del panel, o escribiendo `SALIR` por WhatsApp. El historial se mantiene.

**¿El cliente que me paga necesita tener PagosYa?**
No. Recibe un link, abre la página, escanea el QR con el app de su banco y listo.

**¿Nia lee mis otras conversaciones de WhatsApp?**
No. Funciona en un número propio y dedicado; solo ve los mensajes enviados a ese número.

---

## 📌 Estado del módulo

| | |
|---|---|
| Registro financiero (texto, audio, foto) | ✅ En producción |
| Rajadas de mensajes (varios audios seguidos) | ✅ En producción |
| Recordatorios con envío automático | ✅ En producción |
| Dashboard con realtime y edición de movimientos/recordatorios | ✅ En producción |
| Cobro por WhatsApp | ✅ En producción |
| Confirmación automática de pago | ✅ En producción |
| Créditos "+interacciones" | ✅ En producción |
| Contratación del add-on desde el panel | ⏳ Pendiente — hoy se activa manualmente |
| Número boliviano dedicado | ⏳ Pendiente — opera con número temporal |
