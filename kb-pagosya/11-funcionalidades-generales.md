---
title: Visión general del sistema PagosYa
version: v3
audiencia: merchants
actualizado_en: 2026-05-23
---

# Visión general del sistema PagosYa

PagosYa es un **sistema SaaS híbrido** (web + app móvil) para comercios en Bolivia. Unifica el punto de venta físico, el cobro por QR, la gestión de inventario, la tienda online y los reportes en una sola plataforma.

> Si buscas detalle sobre un módulo específico, consulta el archivo KB correspondiente listado en la sección de referencia al final de este documento.

---

## Módulos del sistema

| Módulo | Descripción breve |
|--------|-------------------|
| **POS (Punto de Venta)** | Cobro con QR automatizado, efectivo, tarjeta. Variantes, descuentos, cupones, turnos de caja. |
| **Inventario** | Productos, categorías, precios, stock, fotos, videos. Alertas de stock mínimo. |
| **Multi-tiendas** | Un solo panel para varias sucursales. Cada tienda con su inventario, empleados y reportes independientes. |
| **Empleados y roles** | Owner, empleado, admin. Acceso por invitación, pin de turno, control de permisos. |
| **Clientes y fidelidad** | Base de clientes, historial de compras, puntos de fidelidad configurables y canje en POS. |
| **Tienda online** | Catálogo digital sincronizado con el POS. Cobro QR/tarjeta/contra entrega. Hosting incluido. |
| **Reportes** | Ventas, artículos, funcionarios, categorías, cupones, turnos. Exportable en CSV y PDF. |
| **Integraciones bancarias** | BNB, Red Enlace (QR y tarjeta 3DS), BANECO, PIX Brasil. |
| **Créditos** | Ampliar límite de ventas (permanente) o agregar tiendas+empleados (30 días) sin cambiar de plan. |
| **Seguridad** | RLS por tienda, JWT, CORS con allowlist, credenciales bancarias cifradas, auditoría de accesos. |

---

## Planes y precios actuales

| Plan | Precio/mes | Precio/año | Límite ventas | Tiendas | Empleados |
|------|-----------|-----------|---------------|---------|-----------|
| **EmprendeYa** | Bs. 79 | Bs. 790 | Bs. 40,000/mes | 1 | 1 |
| **ExpandeYa** | Bs. 169 | Bs. 1,690 | Bs. 80,000/mes | 3 | 3 |
| **ConquistaYa** | Bs. 249 | Bs. 2,490 | Bs. 150,000/mes | 6 | 6 |
| **Plan Checkout Web** | Bs. 249 | Bs. 2,490 | Bs. 150,000/mes | 1 | 1 |
| **RestauranteYa** | Bs. 329 | Bs. 3,290 | Bs. 150,000/mes | 6 | 6 |

**Créditos adicionales:** Bs. 20 por crédito. Cada crédito agrega Bs. 5,000 al límite mensual (permanente) o 1 tienda + 1 empleado por 30 días.

> El plan anual equivale a 10 meses — 2 meses gratis.

---

## Canales de acceso

| Canal | URL / Descripción |
|-------|-------------------|
| **Web (panel admin)** | `app.pagosya.com.bo` |
| **App móvil** | iOS y Android (Capacitor) — mismo panel, optimizado para caja |
| **Tienda online pública** | `{subdominio}.pagosya.shop` o dominio personalizado |
| **Checkout externo** | Enlace de pago para integrar en sitios externos |

---

## Referencia rápida de documentos KB

| Archivo | Contenido |
|---------|-----------|
| `01-planes-precios.md` | Planes, precios y comparativa de características |
| `02-qr-validacion.md` | Cómo funciona el cobro por QR, flujo de validación, bancos |
| `03-multi-tiendas-empleados.md` | Crear tiendas, invitar empleados, roles, geofencing |
| `04-productos-inventario.md` | Crear y gestionar productos, categorías, stock, alertas |
| `05-pos-funcionalidades.md` | Usar el POS, variantes, descuentos, cupones, turnos de caja |
| `06-reportes-analisis.md` | Todos los reportes disponibles, filtros, exportación |
| `07-clientes-fidelidad.md` | Base de clientes, puntos de fidelidad, canje en POS |
| `08-tienda-online.md` | Crear y personalizar tienda online, gestión de pedidos |
| `09-seguridad-apis.md` | Autenticación, roles, RLS, credenciales bancarias, CORS |
| `10-creditos.md` | Comprar y usar créditos, tipos de ampliación, historial |
| `12-integraciones-bancarias.md` | BNB, Red Enlace, BANECO — configuración e integración |
| `13-onboarding-nuevo-usuario.md` | Primeros pasos para un nuevo merchant |
| `14-soporte-asistencia.md` | Canales de soporte, cómo reportar problemas |
| `15-seguridad-datos.md` | Protección de datos del negocio y clientes |
| `16-roadmap-futuro.md` | Funcionalidades próximas |
| `17-glosario.md` | Definición de términos usados en el sistema |
| `23-objeciones-clientes.md` | Respuestas a objeciones frecuentes en ventas |
| `24-script-ventas.md` | Guión para presentar PagosYa a nuevos clientes |
