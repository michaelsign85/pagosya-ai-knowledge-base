# 📋 Plan Checkout Web - Documentación Completa

## 🎯 Resumen Ejecutivo

El **Plan Checkout Web** es un plan especializado de PagosYa diseñado para desarrolladores y empresas que desean integrar pagos QR del Banco Nacional de Bolivia (BNB) en sus propios sitios web, aplicaciones o sistemas mediante una API REST.

---

## 📦 Información del Plan

| Característica | Detalle |
|----------------|---------|
| **Nombre** | Plan Checkout Web |
| **Código interno** | `checkout_web` |
| **Precio promocional** | Bs. 149/primer mes |
| **Precio regular** | Bs. 149/mes |
| **Límite de ventas** | Hasta Bs. 100,000/mes |
| **Tiendas** | 1 tienda |
| **Empleados** | 1 empleado |

---

## ✅ ¿Qué incluye el Plan Checkout Web?

### Funcionalidades Principales

1. **🔗 Checkout Externo / API de Pagos**
   - Endpoint REST para crear sesiones de pago
   - Genera URLs de checkout que puedes enviar a tus clientes
   - Compatible con cualquier plataforma (web, móvil, escritorio)

2. **🌐 Integración con tu Sitio Web**
   - Ejemplos de código en múltiples lenguajes (PHP, JavaScript, Python, cURL)
   - Plugin oficial para WooCommerce disponible
   - Documentación técnica completa en el dashboard

3. **📊 Dashboard de Transacciones**
   - Panel de control exclusivo en `/checkout-web`
   - Visualización de ventas con filtros por período
   - Gestión de API Keys
   - Historial de órdenes y checkouts

4. **🔔 Sistema de Webhooks**
   - Notificaciones automáticas cuando un pago se completa
   - Configuración de URLs de callback (success_url, cancel_url)
   - Integración con sistemas de e-commerce

5. **💰 Límite de Ventas Generoso**
   - Hasta Bs. 100,000 en ventas mensuales
   - Ideal para tiendas online medianas y grandes

---

## 🎯 ¿Para quién es este plan?

El Plan Checkout Web es ideal para:

- ✅ **Desarrolladores** que quieren integrar pagos QR en sus aplicaciones
- ✅ **Tiendas online** con sitio web propio (WordPress, Shopify, custom)
- ✅ **Empresas** que necesitan cobrar a través de su propio sistema
- ✅ **Agencias** que desarrollan soluciones para clientes
- ✅ **Negocios** que ya tienen presencia web y quieren agregar pagos QR
- ✅ **Usuarios de WooCommerce** (plugin oficial disponible)

### NO es ideal para:

- ❌ Negocios que solo necesitan punto de venta físico (mejor EmprendeYa o ExpandeYa)
- ❌ Quienes necesitan tienda online incluida (mejor ConquistaYa)
- ❌ Negocios muy pequeños con pocas ventas (mejor EmprendeYa)

---

## 🔄 Comparación con Otros Planes

| Característica | EmprendeYa | ExpandeYa | ConquistaYa | **Checkout Web** |
|----------------|------------|-----------|-------------|------------------|
| **Precio** | Bs. 49/mes | Bs. 99/mes | Bs. 150/mes | **Bs. 149/mes** |
| **Límite ventas** | Bs. 30,000 | Bs. 60,000 | Bs. 120,000 | **Bs. 100,000** |
| **Tiendas** | 1 | 3 | 6 | **1** |
| **Empleados** | 1 | 3 | 6 | **1** |
| **Caja básica** | ✅ | ✅ | ✅ | ❌ |
| **POS completo** | ❌ | ✅ | ✅ | ❌ |
| **Tienda online** | ❌ | ❌ | ✅ | ❌ |
| **API/Checkout externo** | ❌ | ❌ | ❌ | **✅** |
| **Dashboard dedicado** | ❌ | ❌ | ❌ | **✅** |
| **Webhooks** | ❌ | ❌ | ❌ | **✅** |

---

## 🛠️ Cómo Funciona

### Flujo de Pago

1. **Tu sistema** llama a la API de PagosYa con los datos del pedido
2. **PagosYa** crea una sesión de checkout y devuelve una URL
3. **El cliente** accede a la URL y ve el monto a pagar
4. **El cliente** genera el QR y paga con su banco
5. **PagosYa** notifica a tu sistema (webhook) cuando el pago está confirmado
6. **Tu sistema** procesa el pedido como pagado

### Endpoint de la API

```
POST https://nbjwpakpimrqfocsxkda.supabase.co/functions/v1/create-external-checkout
```

### Headers Requeridos

| Header | Valor |
|--------|-------|
| `Authorization` | `Bearer TU_API_KEY` |
| `apikey` | Anon key de Supabase (pública) |
| `Content-Type` | `application/json` |

### Parámetros de la Solicitud

| Campo | Tipo | Requerido | Descripción |
|-------|------|-----------|-------------|
| `amount` | number | ✅ | Monto en Bolivianos (ej: 150.50) |
| `currency` | string | ✅ | Siempre "BOB" |
| `order_id` | string | ✅ | ID único de tu pedido |
| `success_url` | string | ❌ | URL a redirigir tras pago exitoso |
| `cancel_url` | string | ❌ | URL a redirigir si cancela |
| `customer.name` | string | ❌ | Nombre del cliente |
| `customer.email` | string | ❌ | Email del cliente |
| `customer.phone` | string | ❌ | Teléfono del cliente |
| `customer.nit` | string | ❌ | NIT para facturación |
| `expiration_minutes` | number | ❌ | Minutos hasta expirar (default: 60) |
| `metadata` | object | ❌ | Datos adicionales personalizados |

### Respuesta Exitosa

```json
{
  "success": true,
  "checkout_id": "uuid-del-checkout",
  "checkout_url": "https://www.pagosya.com.bo/pay/uuid-del-checkout",
  "expires_at": "2025-11-28T12:00:00Z"
}
```

---

## 🔑 API Keys

Los usuarios del Plan Checkout Web deben:

1. Acceder a `/checkout-web/api-keys` en su dashboard
2. Crear una nueva API Key (comienza con `pk_live_`)
3. Guardar la key de forma segura (solo se muestra una vez)
4. Usar la key en el header `Authorization: Bearer pk_live_xxxxx`

**Importante:** Las API Keys son secretas. Nunca compartir públicamente.

---

## 🔌 Plugin WooCommerce

Para usuarios de WordPress/WooCommerce, ofrecemos un **plugin oficial gratuito**:

- **Nombre:** PagosYa Payment Gateway
- **Versión:** 1.1.0
- **Compatibilidad:** WordPress 6.0+, WooCommerce 7.0+
- **Instalación:** Descargar desde el dashboard o WordPress.org

El plugin automatiza todo el proceso de integración sin necesidad de programar.

---

## 📞 Preguntas Frecuentes

### ¿Puedo usar el Plan Checkout Web junto con otro plan?

No directamente. Cada cuenta tiene un plan activo. Sin embargo, puedes:
- Usar Checkout Web si solo necesitas la API
- Usar ConquistaYa si también necesitas tienda online y POS

### ¿Qué pasa si supero el límite de Bs. 100,000/mes?

El sistema te notificará cuando estés cerca del límite. Si necesitas más capacidad, contacta a soporte para opciones enterprise.

### ¿Necesito conocimientos técnicos?

- **Con WooCommerce:** No, el plugin hace todo automáticamente
- **Integración custom:** Sí, necesitas saber programar o tener un desarrollador

### ¿Cuánto tarda en activarse?

El plan se activa inmediatamente después del pago. Puedes empezar a usar la API en minutos.

### ¿Funciona con todos los bancos?

El pago QR es procesado por el Banco Nacional de Bolivia (BNB). Tus clientes pueden pagar desde cualquier banco que soporte pagos QR.

### ¿Hay comisión por transacción?

No hay comisión adicional de PagosYa. Solo pagas la mensualidad del plan.

---

## 📍 Acceso al Dashboard

Los usuarios con Plan Checkout Web tienen acceso a:

- `/checkout-web` - Dashboard principal con métricas
- `/checkout-web/api-keys` - Gestión de API Keys
- `/checkout-web/orders` - Historial de checkouts
- `/checkout-web/webhooks` - Configuración de webhooks
- `/checkout-web/docs` - Documentación y ejemplos de código

---

## 🆘 Soporte

Para dudas sobre el Plan Checkout Web:

- **Dashboard:** Sección de ayuda en el panel
- **Email:** soporte@pagosya.com.bo
- **WhatsApp:** Chat de soporte disponible

---

## 📅 Información de Versión

- **Fecha de lanzamiento:** Noviembre 2025
- **Última actualización:** 28 de noviembre de 2025
- **Versión del documento:** 1.0

---

*Este documento está destinado a la memoria de la IA atendente de PagosYa para responder consultas de usuarios sobre el Plan Checkout Web.*
