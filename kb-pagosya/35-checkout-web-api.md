---
title: Checkout Web, API, sandbox y documentación para developers
version: v1
audiencia: developers, merchants, soporte, ventas
actualizado_en: 2026-08-02
---

# Checkout Web: API, sandbox y documentación para developers

Este documento es la fuente principal para responder preguntas sobre la API Checkout Web de PagosYa, el sandbox, las credenciales, los webhooks y el paso a producción.

---

## Respuesta rápida para atención

Si una persona solicita la documentación de la API o pregunta cómo integrar PagosYa, responder:

> Puedes consultar la documentación pública de Checkout Web aquí: https://www.pagosya.com.bo/developers
>
> En esa misma página puedes revisar ejemplos y solicitar una API key de sandbox. El sandbox genera un QR ficticio no pagable y no mueve fondos. Cuando la integración esté lista, puedes activar el Plan Checkout Web y configurar producción desde tu dashboard.

Si pide una demostración, agregar:

> Puedes ver la tienda demo aquí: https://www.pagosya.com.bo/developers/demo

No enviar API keys por chat. Las claves sandbox se entregan por correo después de revisar la solicitud.

---

## URLs oficiales

| Recurso | URL | Acceso |
|---|---|---|
| Documentación pública y solicitud sandbox | https://www.pagosya.com.bo/developers | Público |
| Tienda de demostración | https://www.pagosya.com.bo/developers/demo | Público |
| Landing comercial | https://www.pagosya.com.bo/checkout-web-pagosya | Público |
| Soporte | soporte@pagosya.com.bo | Público |
| Dashboard Checkout Web | https://www.pagosya.com.bo/checkout-web | Requiere login y plan activo |
| API keys de producción | https://www.pagosya.com.bo/checkout-web/api-keys | Requiere login y plan activo |
| Webhooks de producción | https://www.pagosya.com.bo/checkout-web/webhooks | Requiere login y plan activo |
| Órdenes | https://www.pagosya.com.bo/checkout-web/orders | Requiere login y plan activo |
| Documentación privada | https://www.pagosya.com.bo/checkout-web/docs | Requiere login y plan activo |
| Referencia privada de API | https://www.pagosya.com.bo/checkout-web/docs/api | Requiere login y plan activo |

La automatización debe enviar por defecto https://www.pagosya.com.bo/developers cuando alguien pregunte por documentación, API, sandbox, integración o credenciales de prueba.

---

## Qué es Checkout Web

Checkout Web permite que una página, tienda virtual, aplicación o sistema externo cree un checkout de pago QR mediante API. El comercio crea el checkout desde su backend, muestra o redirige al cliente al QR y recibe la confirmación.

Flujo:

1. El backend del developer llama a PagosYa.
2. PagosYa devuelve un identificador y un QR.
3. El cliente paga en producción.
4. PagosYa confirma el estado.
5. PagosYa envía `checkout.completed` al webhook configurado.
6. El developer valida la firma y acredita el pedido una sola vez.
7. La venta aparece en PagosYa con el canal **Checkout Web**.

El valor técnico del canal es `external_checkout`; la interfaz lo muestra como **Checkout Web**.

---

## Sandbox

El sandbox permite construir la integración sin pagos reales.

### Permite validar

- autenticación con API key;
- estructura del JSON y campos obligatorios;
- respuestas, errores y rate limit;
- generación de un QR ficticio;
- relación entre `order_id` y `checkout_id`.

### No hace

- el QR no puede pagarse;
- no se conecta a una cuenta bancaria;
- no mueve dinero;
- no confirma pagos;
- no envía callbacks o webhooks en esta primera fase.

El callback se valida después en producción mediante un pago real controlado de Bs. 0,10 o Bs. 1.

### Solicitar credenciales

1. Entrar a https://www.pagosya.com.bo/developers
2. Completar **Solicitar acceso**.
3. Informar nombre, correo profesional, WhatsApp, empresa/proyecto y caso de uso.
4. El sitio web o nombre de aplicación es opcional.
5. PagosYa revisa la solicitud.
6. Si se aprueba, el developer recibe por correo una clave `sk_test_...`.

### Endpoint sandbox

```text
POST https://nbjwpakpimrqfocsxkda.supabase.co/functions/v1/sandbox-create-checkout
```

Headers:

```text
Authorization: Bearer sk_test_TU_CLAVE
Content-Type: application/json
```

Ejemplo:

```json
{
  "amount": 1.00,
  "currency": "BOB",
  "order_id": "pedido-1001",
  "success_url": "https://mitienda.com/pago/exitoso",
  "cancel_url": "https://mitienda.com/pago/cancelado",
  "customer": { "name": "Cliente de prueba", "email": "cliente@ejemplo.com" },
  "metadata": { "source": "integration-test" },
  "expiration_minutes": 15
}
```

La documentación pública contiene ejemplos para cURL, Node.js, PHP, Python, C#/.NET y Java.

### Campos

| Campo | Obligatorio | Descripción |
|---|---|---|
| `amount` | Sí | Monto positivo; no produce un cobro real en sandbox. |
| `currency` | No | Actualmente `BOB`; predeterminado `BOB`. |
| `order_id` | No | Referencia única de hasta 120 caracteres. |
| `success_url` | Sí | URL de retorno satisfactorio. |
| `cancel_url` | Sí | URL de retorno por cancelación. |
| `customer` | No | Datos básicos opcionales. |
| `metadata` | No | Datos propios para relacionar checkout y pedido. |
| `expiration_minutes` | No | De 5 a 1.440 minutos; predeterminado 30. |

### Respuesta

La respuesta HTTP `201` incluye normalmente `checkout_id`, `order_id`, `amount`, `currency`, `status: pending`, `livemode: false`, `environment: sandbox`, `qr_code`, `qr_image`, `expires_at` y un aviso de QR ficticio no pagable.

### Errores habituales

| HTTP | Significado |
|---|---|
| `400` | Monto, moneda, URLs, `order_id` o JSON inválidos. |
| `401` | API key inválida, revocada o de ambiente incorrecto. |
| `409` | `order_id` duplicado para la misma API key. |
| `413` | `customer` o `metadata` demasiado grandes. |
| `429` | Límite excedido; revisar `Retry-After`. |
| `500` | Error temporal; evitar pedidos duplicados al reintentar. |

Rate limit predeterminado: 60 solicitudes por minuto por API key.

---

## Producción

Producción funciona dentro del dashboard normal de PagosYa. No hay un dashboard separado para developers sandbox.

Checklist:

1. Completar las pruebas de sandbox.
2. Contratar y activar el Plan Checkout Web.
3. Configurar una integración bancaria habilitada.
4. Generar credenciales en **Checkout Web → API Keys**.
5. Registrar una URL HTTPS en **Checkout Web → Webhooks**.
6. Guardar la Clave Secreta HMAC solo en el backend.
7. Cambiar endpoint y credenciales de sandbox por producción.
8. Probar con Bs. 0,10 o Bs. 1.
9. Verificar QR, confirmación, webhook, firma, pedido y reporte.

### Credenciales

- `pk_live_...`: API Key enviada en `Authorization: Bearer` para crear y consultar checkouts.
- `sk_live_...`: clave secreta asociada; debe protegerse según la documentación privada.
- **Clave Secreta HMAC**: credencial diferente usada exclusivamente para verificar webhooks.

No usar `sk_live_...` como secreto HMAC. Nunca exponer claves live en React, navegador, app móvil, repositorio, captura o chat.

### Endpoints

Crear checkout:

```text
POST https://nbjwpakpimrqfocsxkda.supabase.co/functions/v1/create-external-checkout
```

Consultar estado:

```text
GET https://nbjwpakpimrqfocsxkda.supabase.co/functions/v1/get-checkout-status?checkout_id=<UUID>
```

Autenticación para ambos:

```text
Authorization: Bearer pk_live_TU_API_KEY
```

La creación devuelve normalmente `checkout_id`, `checkout_url`, `status_url`, monto, moneda, estado, expiración, proveedor, referencia y datos del QR. El sistema del developer debe guardar la relación entre `order_id` y `checkout_id`.

---

## Webhooks

Evento de confirmación:

```text
checkout.completed
```

Headers:

```text
X-PagosYa-Signature: <firma_hmac_sha256>
X-PagosYa-Event: checkout.completed
X-PagosYa-Checkout-Id: <checkout_id>
Content-Type: application/json
User-Agent: PagosYa-Webhook/1.0
```

Buenas prácticas:

1. Leer el cuerpo HTTP original.
2. Calcular HMAC-SHA256 con la Clave Secreta HMAC.
3. Comparar la firma hexadecimal lowercase de forma segura.
4. Verificar evento, monto, moneda, referencia y checkout.
5. Confirmar `completed` mediante `get-checkout-status` como defensa adicional.
6. Procesar cada checkout una sola vez.
7. Responder rápidamente con HTTP `2xx`.
8. Tratar reenvíos de forma idempotente.

No se garantiza un rango fijo de IPs. La autenticidad se valida oficialmente mediante HMAC.

---

## Seguridad y alcance financiero

Las integraciones bancarias disponibles permiten consulta, generación de QR y confirmación de pagos.

- No existe API de cash-out.
- No existe retiro.
- No existe transferencia de fondos del usuario.
- La API key no permite mover dinero desde la cuenta del comercio.

Las claves siguen siendo confidenciales porque permiten crear y consultar operaciones.

---

## Tienda demo

URL: https://www.pagosya.com.bo/developers/demo

La tienda ficticia Lúmina demuestra selección de productos, carrito, datos del cliente, sandbox/producción, QR, consulta automática del estado, modal de pago confirmado, recibo ficticio y retorno a la tienda.

En producción usa valores bajos para demostraciones controladas. Un pago real solo debe realizarse con autorización.

---

## Preguntas frecuentes para la automatización

### ¿Dónde está la documentación?

En https://www.pagosya.com.bo/developers. Incluye sandbox, solicitud de acceso, campos y ejemplos.

### ¿Cómo obtengo una API key de prueba?

Completa el formulario público. PagosYa revisará la solicitud y, si se aprueba, enviará una clave `sk_test_...` por correo.

### ¿Necesito tener página web?

No. El campo es opcional. Puede integrarse en una app, ERP, software propio, tienda virtual u otro sistema.

### ¿El QR sandbox se puede pagar?

No. Es ficticio, no pagable y sin conexión bancaria.

### ¿Sandbox envía webhook?

No en la fase actual. El webhook se prueba en producción con un pago controlado de Bs. 0,10 o Bs. 1.

### ¿Puedo llamar desde React o una app móvil?

No directamente. La clave debe permanecer en el backend propio del developer.

### ¿Qué cambia al pasar a producción?

El endpoint y las credenciales. Producción requiere plan activo, banco configurado, API key live y webhook.

### ¿Permite retirar o transferir dinero?

No. No existe cash-out, retiro ni transferencia.

### ¿Dónde veo las operaciones?

En **Checkout Web → Órdenes**. Las ventas confirmadas también aparecen en reportes con canal **Checkout Web**.

### ¿Dónde configuro el webhook?

En https://www.pagosya.com.bo/checkout-web/webhooks, con login y Plan Checkout Web activo.

### ¿La documentación de producción es pública?

La introducción y el sandbox son públicos. La referencia completa de producción está dentro del dashboard del plan activo.

---

## Reglas para soporte y automatización

- Enviar primero https://www.pagosya.com.bo/developers.
- Enviar la demo solo si piden ver el funcionamiento.
- Explicar que sandbox no procesa pagos ni webhooks.
- No prometer aprobación automática de credenciales.
- No pedir ni recibir API keys, HMAC secrets o credenciales bancarias por chat.
- No inventar endpoints, precios, plazos o funciones.
- Para producción, indicar que se requiere plan e integración bancaria activos.
- Para errores, pedir código HTTP, mensaje, `checkout_id` u `order_id`, nunca la clave completa.
- Derivar casos no resueltos a soporte@pagosya.com.bo.
