---
title: Soporte y asistencia
version: v3
audiencia: merchants
actualizado_en: 2026-05-23
---

# Soporte y asistencia

PagosYa ofrece un sistema de soporte integrado directamente en el panel de control. El merchant puede crear tickets de soporte, hacer seguimiento del estado y conversar con el equipo de soporte sin salir del sistema.

---

## Sección 1 — Acceso al módulo de Soporte

El módulo de soporte se encuentra en el menú lateral izquierdo con el ícono de **"Soporte"** (HelpCircle).

Al ingresar, el merchant ve:
- La lista de todos sus tickets creados anteriormente (ordenados por fecha, más reciente primero).
- El estado actual de cada ticket con su código de referencia.
- El botón **"Nuevo Ticket"** para crear una nueva solicitud.

---

## Sección 2 — Crear un ticket de soporte

### Paso a paso

1. Ir al menú lateral → **Soporte**.
2. Hacer clic en el botón **"+ Nuevo Ticket"** (esquina superior derecha).
3. Completar el formulario:

### Sección: Información de Contacto

| Campo | Descripción | Requerido |
|---|---|---|
| **Nombre completo** | Se pre-llena automáticamente con el nombre del usuario logueado | Sí |
| **Email** | Se pre-llena con el email de la cuenta | No (recomendado) |
| **Teléfono de contacto** | Número para contacto adicional (ej: +591 7XXXXXXX) | No |

### Sección: Detalles del Ticket

| Campo | Descripción | Requerido |
|---|---|---|
| **Asunto** | Breve descripción de la solicitud (ej: "Error al generar QR de pago") | Sí |
| **Categoría** | Tipo de consulta (ver tabla de categorías abajo) | No (default: Consulta General) |
| **Prioridad** | Nivel de urgencia (ver tabla abajo) | No (default: Normal) |
| **Descripción** | Descripción detallada del problema o solicitud (mínimo una descripción clara) | Sí |
| **Adjuntar imágenes** | Capturas de pantalla del error o evidencia (máximo 5 imágenes) | No |

4. Hacer clic en **"Enviar Ticket"**.
5. El ticket aparece inmediatamente en la lista con estado **"Abierto"**.

---

## Sección 3 — Categorías y prioridades

### Categorías disponibles

| Valor | Etiqueta |
|---|---|
| `general` | Consulta General |
| `technical` | Problema Técnico |
| `billing` | Facturación / Pagos |
| `feature` | Solicitud de Funcionalidad |
| `bug` | Reportar Error |
| `account` | Mi Cuenta |

> **Consejo:** Elegir la categoría correcta ayuda al equipo de soporte a derivar el ticket al especialista adecuado más rápido.

### Prioridades disponibles

| Valor | Etiqueta | Cuándo usarla |
|---|---|---|
| `low` | Baja | Consultas no urgentes, sugerencias |
| `normal` | Normal | Problemas que no bloquean la operación |
| `high` | Alta | Problemas que dificultan la operación diaria |
| `urgent` | Urgente | El negocio está completamente bloqueado |

---

## Sección 4 — Estados del ticket

Cada ticket avanza por los siguientes estados:

| Estado | Descripción |
|---|---|
| **Abierto** | Ticket recibido, pendiente de revisión |
| **En Proceso** | El equipo de soporte está trabajando en el caso |
| **Esperando Respuesta** | El equipo de soporte necesita más información del merchant |
| **Resuelto** | El problema fue solucionado |
| **Cerrado** | El ticket fue cerrado (no se pueden enviar más mensajes) |

> Cuando el estado es **"Esperando Respuesta"**, revisar el ticket y responder en la conversación interna para continuar la atención.

---

## Sección 5 — Conversación interna del ticket

Cada ticket tiene un hilo de conversación tipo chat entre el merchant y el equipo de soporte.

### Cómo funciona

1. Abrir un ticket existente desde la lista (hacer clic sobre él).
2. Ver la descripción original del ticket con los datos de contacto.
3. Leer los mensajes del equipo de soporte (aparecen a la izquierda con el ícono 🛡️ Soporte).
4. Escribir una respuesta en el campo de texto inferior.
5. Presionar **Enter** o el botón verde de envío.

### Comportamiento visual

- Los mensajes del **merchant** aparecen a la **derecha** (burbuja verde).
- Los mensajes del **equipo de soporte** aparecen a la **izquierda** (burbuja gris).
- El historial se desplaza automáticamente al último mensaje.

> Si el ticket está en estado **"Cerrado"**, el campo de mensaje desaparece y no se pueden enviar más respuestas. Si se necesita continuar, abrir un nuevo ticket.

---

## Sección 6 — Ver notas del equipo de soporte

Cuando el equipo de soporte agrega una nota administrativa al ticket, aparece un bloque amarillo al final del ticket con el texto:

> **Nota del equipo de soporte:** [texto de la nota]

Estas notas pueden contener instrucciones específicas, soluciones o pasos adicionales que el merchant debe seguir.

---

## Sección 7 — Adjuntar imágenes

Tanto al crear el ticket como en la conversación posterior, es posible adjuntar imágenes:

- Formatos aceptados: cualquier imagen (`image/*`)
- Máximo **5 archivos** por ticket al momento de crearlo
- Las imágenes se suben automáticamente al storage de PagosYa
- Se visualizan como enlaces clicables dentro del ticket

> Adjuntar capturas de pantalla acelera significativamente la resolución del problema.

---

## Sección 8 — Código de referencia del ticket

Cada ticket tiene un **ID único** que se muestra en el detalle del ticket como:

```
#a3f2b1c0
```

Este código corresponde a los primeros 8 caracteres del ID interno. Guardar este código para hacer referencia al ticket en cualquier comunicación adicional con el equipo de soporte.

---

## Sección 9 — Canales de contacto adicionales

Además del sistema de tickets integrado, PagosYa ofrece:

| Canal | Disponibilidad | Uso recomendado |
|---|---|---|
| **Sistema de tickets** (en el panel) | 24/7 — respuesta en horario laboral | Problemas técnicos, facturación, reportes de error |
| **Chat IA** (widget flotante en el panel) | 24/7 automático | Consultas frecuentes, guías de uso, dudas rápidas |
| **WhatsApp** | Lunes a sábado, 09:00–19:00 | Consultas urgentes que requieren atención inmediata |
| **Correo electrónico** | soporte@pagosya.com.bo | Documentación formal, contratos, integraciones bancarias |

> El **Chat IA** disponible en el panel responde automáticamente a la mayoría de consultas sobre el uso del sistema. Se recomienda consultarlo primero antes de crear un ticket.

---

## FAQ — Preguntas frecuentes

**¿Cuánto tiempo tarda en responderse un ticket?**
El equipo de soporte atiende en horario laboral (lunes a sábado, 09:00–19:00). Los tickets urgentes tienen prioridad de atención.

**¿Puedo adjuntar capturas de pantalla?**
Sí. Al crear el ticket, se pueden adjuntar hasta 5 imágenes. Las imágenes son fundamentales para diagnosticar problemas técnicos.

**¿Qué hago si el estado del ticket dice "Esperando Respuesta"?**
El equipo de soporte necesita más información. Ingresar al ticket y responder en la conversación interna con los datos solicitados.

**¿Puedo ver los tickets antiguos?**
Sí. Todos los tickets del usuario aparecen en la lista principal del módulo de Soporte, ordenados del más reciente al más antiguo.

**¿Qué categoría elegir si no sé cuál es mi problema?**
Usar "Consulta General". El equipo de soporte reclasificará el ticket si es necesario.

**¿El empleado también puede crear tickets?**
Sí. Cualquier usuario con sesión iniciada (propietario o empleado) puede acceder al módulo de Soporte y crear tickets.

**¿Qué pasa si cierro el ticket por error?**
Los tickets cerrados no se pueden reabrir. En ese caso, crear un nuevo ticket haciendo referencia al código del ticket anterior.
