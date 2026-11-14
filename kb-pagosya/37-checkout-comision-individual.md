---
title: Checkout Web individual por comisión, activación y liquidación
version: v1
audiencia: developers, comercios, soporte, ventas
actualizado_en: 2026-11-13
---

# Checkout Web individual por comisión

Para una empresa que integra cobros QR en su sitio, aplicación o sistema y prefiere pagar por ventas confirmadas, sin mensualidad de Checkout Web. Para administrar comercios de terceros, consultar `38-checkout-saas-proveedores.md`.

## Comisión individual: tarifas vigentes

| Modalidad por comisión | Comisión PagosYa | Activación única | Mensualidad | Volumen de ventas del plan |
|---|---|---|---|---|
| Embedded, con marca PagosYa | 1% | Bs. 49,90 | Sin mensualidad | Sin tope comercial |
| White Label, sin marca PagosYa | 2% | Bs. 49,90 | Sin mensualidad | Sin tope comercial |

La activación individual se paga una sola vez en una contratación nueva, no cada ciclo ni cada mes. No se cobra retroactivamente a cuentas por comisión ya activas. Las condiciones se muestran antes de contratar; para una cuenta existente rigen su tasa, ciclo y plazo aceptados, que PagosYa puede configurar.

Los planes mensuales de Checkout Web siguen disponibles por separado, con mensualidad, límite de ventas y 0% de comisión PagosYa. No sumar automáticamente mensualidad y porcentaje al mismo contrato individual.

## Comisión individual: qué operaciones cuentan

La comisión se acumula al confirmar un pago por la **API Checkout Web** o por **Venta Rápida del dashboard** de la cuenta por comisión. Crear un QR pendiente, fallido o sin pago confirmado no devenga comisión.

Una venta confirmada de Bs. 100 genera Bs. 1 en Embedded al 1%, o Bs. 2 en White Label al 2%. No se cobra por número de solicitudes a la API. El porcentaje no se extiende automáticamente a POS, tienda online u otros canales.

El comprador paga en el banco del comercio. PagosYa no retiene ni descuenta el porcentaje de esos fondos: la comisión se factura y se paga aparte por QR institucional a PagosYa. La activación única también se paga a PagosYa. Las tarifas bancarias son independientes.

## Comisión individual: contratación y producción

En https://www.pagosya.com.bo/planes elegir Checkout Web **por comisión**, Embedded 1% o White Label 2%. Crear la cuenta o iniciar sesión, aceptar las condiciones y pagar la activación única de Bs. 49,90 por QR. La modalidad solo se activa tras confirmar el pago.

Después se completa la integración bancaria, se valida la conexión y se configura la API key de producción y el webhook desde Checkout Web. Sandbox no activa producción. Si ya existe otra suscripción o deuda, revisar la cuenta con soporte; no prometer migración automática ni crear otra cuenta para evitar obligaciones.

El plan no incluye por sí solo POS, inventario, facturación SIAT o WhatsApp CRM. Sin tope comercial de ventas no significa solicitudes ilimitadas: permanecen los límites técnicos, permisos y restricciones bancarias.

## Comisión individual: ciclo abierto, cierre y plazo

La oferta estándar cierra cada **7 días** y concede **24 horas** desde el cierre para liquidar la factura. Siempre consultar las fechas del panel y las condiciones de esa cuenta.

El ciclo abierto muestra comisión en formación y todavía no es una factura exigible. Por eso Pagar comisión puede estar deshabilitado antes del cierre. Un valor pequeño con decimales no significa que se perdió la comisión.

Todo cierre con importe a liquidar requiere pago, **sin monto mínimo comercial**. Se paga el importe de la factura emitida, dentro de su plazo. El siguiente ciclo continúa acumulando mientras se liquida el anterior; pagar una factura no borra las comisiones del ciclo nuevo.

## Comisión individual: pago, contador y bloqueo

El card **Comisión API** del dashboard muestra el ciclo y el saldo pendiente. Si hay factura cerrada, **Pagar comisión** genera su QR en el mismo panel. El contador muestra el tiempo restante hasta el vencimiento y el sistema consulta la confirmación del pago. Historial: https://www.pagosya.com.bo/checkout-web/comisiones.

El widget financiero para un panel externo es opcional; no es necesario instalarlo para que PagosYa registre las comisiones. No prometer validación en un número fijo de segundos: depende del banco. Si el cliente ya pagó, no pedir otro pago; consultar el estado y, si persiste, derivar a soporte@pagosya.com.bo.

Una factura vencida sin pagar bloquea **nuevos cobros QR de esa cuenta**. Los pagos anteriores siguen pudiendo confirmarse y se mantiene la posibilidad de liquidar la deuda. La generación se habilita tras confirmar el pago si no queda otro motivo de bloqueo. No confundir el bloqueo con retención de fondos o eliminación de datos.

## Comisión individual: respuestas rápidas

**¿Puedo usar la API sin mensualidad?** Sí: Embedded 1% o White Label 2%, con activación individual de Bs. 49,90 una sola vez. La comisión alcanza pagos confirmados por API y Venta Rápida del dashboard.

**¿Por qué no puedo pagar lo que aparece en el ciclo?** Puede estar abierto. Revisar si existe una factura cerrada y su vencimiento; el saldo en formación no se paga anticipadamente desde ese botón.

**¿Necesito llegar a un mínimo?** No hay mínimo comercial: se liquida el importe de cada factura cerrada según su vencimiento.

**¿Puedo seguir cobrando durante el plazo?** Sí, mientras la cuenta esté habilitada. El ciclo siguiente acumula; al vencer una factura impaga se bloquean nuevos cobros.

**¿Tengo un SaaS con varios comercios?** Usar el plan SaaS: el proveedor paga mensualidad y cada afiliado su comisión. Su activación está incluida; no cobrar Bs. 49,90 por afiliado.

Documentación y formulario sandbox: https://www.pagosya.com.bo/developers. Comparación mensual: `35-checkout-web-api.md`. SaaS: https://www.pagosya.com.bo/developers?producto=saas. Para soporte pedir referencia, horario y error; nunca claves API, secretos HMAC o contraseñas bancarias por chat.
