---
title: Checkout Web para proveedores SaaS, integración global y comisiones
version: v1
audiencia: proveedores SaaS, developers, soporte, ventas
actualizado_en: 2026-11-13
---

# Checkout Web para proveedores SaaS — versión beta

PagosYa para SaaS permite que un proveedor de POS, ERP u otro software conecte los bancos de sus comercios desde una integración global. El proveedor paga una mensualidad por capacidad de afiliados. Cada comercio cobra en su propio banco y paga su comisión a PagosYa.

**Versión beta:** reportar errores a **soporte@pagosya.com.bo**. Beta no significa sandbox, prueba gratuita automática o ausencia de límites.

## SaaS: precios y capacidad del proveedor

| Plan SaaS | Precio de lanzamiento mensual | Comercios afiliados |
|---|---|---|
| Inicial | Bs. 49,90/mes | Hasta 10 |
| Crecimiento | Bs. 99,90/mes | Hasta 50 |
| Escala | Bs. 249,90/mes | Hasta 200 |

Los planes SaaS son mensuales, sin aplicar automáticamente la promoción anual de otros productos. Consultar la tarifa mostrada al contratar; cotizaciones y períodos ya pagados conservan sus condiciones registradas.

El cupo se reserva al **crear o invitar** al comercio, incluso antes de conectar su banco. No decir que solo cuentan bancos conectados ni que pausar o alternar empresas permite reutilizar cupos del mismo período. Consultar la capacidad real del panel.

## SaaS: quién paga cada concepto

El **proveedor** paga la mensualidad Inicial, Crecimiento o Escala. El **comercio afiliado** paga a PagosYa **Embedded 1%** con marca o **White Label 2%** sin marca, sobre los cobros confirmados alcanzados por el plan.

La activación del afiliado está incluida: **no se cobran los Bs. 49,90 de la contratación individual a cada afiliado SaaS**. El administrador del SaaS acuerda y elige 1% o 2%; el titular del comercio acepta sus condiciones antes de operar.

Ejemplo SaaS: el proveedor Inicial paga Bs. 49,90/mes para hasta 10 comercios. Si un afiliado Embedded confirma Bs. 100, acumula Bs. 1; otro White Label que confirma Bs. 100 acumula Bs. 2. No multiplicar la mensualidad por el número de comercios ni confundirla con el porcentaje.

El dinero de cada venta llega al banco del comercio. PagosYa no retiene el porcentaje de esa venta; las comisiones se liquidan aparte por QR institucional. No es una comisión pagada al proveedor ni un programa de referidos.

## SaaS: integración global una sola vez

El proveedor desarrolla en su backend **una API global y un webhook global** para toda la plataforma. Instala el menú **Integración bancaria** y, si lo desea, **Comisiones** en el panel de las empresas que habiliten cobros QR.

Cada empresa queda vinculada con su propio comercio afiliado, banco y condiciones. Se reutiliza el mismo módulo: no se repite el desarrollo ni se copia manualmente una API key de producción o un webhook por usuario.

El backend guarda la clave global, autentica al operador y autoriza su acceso a la empresa antes de abrir sesiones o cobrar. Un identificador enviado por el navegador no autoriza a operar con otro comercio.

Guía, ejemplos y referencia del endpoint **saas-platform**: **https://www.pagosya.com.bo/developers?producto=saas**. No inventar acciones ni usar la clave de sandbox para administrar afiliados.

## SaaS: contratación del proveedor y producción

1. Elegir el plan en https://www.pagosya.com.bo/planes#saas y crear o usar la cuenta del proveedor.
2. Registrar la plataforma y esperar la revisión de PagosYa. Elegir un card todavía no equivale a aprobación.
3. Tras la aprobación, cotizar y pagar la mensualidad por QR desde https://www.pagosya.com.bo/plataformas.
4. Configurar la clave global, los orígenes autorizados y el webhook global en el backend.
5. Crear cada comercio, obtener su consentimiento y completar su integración bancaria y validación.
6. Homologar con operaciones reales controladas antes de habilitar la cartera completa.

Un mes gratuito concedido expresamente para un piloto no es una oferta automática. El atendente no puede concederlo ni prometerlo a todos.

## SaaS: formulario bancario sin otro login

Desde el menú del SaaS se abre una **página segura alojada por PagosYa**. El comercio gestionado **no necesita otra cuenta ni login de PagosYa**. El formulario y las credenciales se envían a PagosYa; el proveedor recibe el estado, no contraseñas ni la clave AES.

El menú es permanente. Su enlace abre una sesión bancaria de **30 minutos** y se renueva en cada acceso; el registro y los datos del trámite permanecen guardados.

El titular completa el formulario de Banco Económico y sigue la solicitud/carta. Cuando el banco envíe usuario, contraseña y cuenta, vuelve al **mismo menú** del SaaS y guarda sus credenciales en una sesión nueva. No necesita conservar el primer enlace ni terminar todo antes de su vencimiento.

PagosYa configura la clave AES y prueba la conexión desde su administración. Enviar el formulario o guardar credenciales no habilita todavía cobros: el estado debe indicar **conectado**, con validación aprobada. No prometer un plazo fijo de aprobación del banco.

El iframe es una alternativa con origen HTTPS autorizado; no insertar cualquier enlace temporal en un iframe. Nunca pedir credenciales por WhatsApp o correo. Si el comercio ya tiene banco, plan o deuda en PagosYa, solicitar vinculación asistida a soporte para preservar su historial; no crear otra identidad para evitar obligaciones.

## SaaS: qué hace el owner después de conectar el banco

El owner ve el estado conectado y crea cobros desde su **misma API global**, indicando el afiliado autorizado. PagosYa genera y vincula internamente la clave de producción del comercio. El owner no tiene que copiarla ni pegarla en cada usuario.

Cada cobro usa el banco del comercio correspondiente. Verificar el pago por webhook global o consulta de estado desde el backend, con comercio, referencia, monto y moneda. Un QR mostrado o una redirección de éxito no prueban pago. Validar firma del webhook y procesar eventos de forma idempotente según la documentación.

## SaaS: comisión y panel de liquidación

La comisión alcanza pagos confirmados por la API y Venta Rápida del dashboard cuando la cuenta usa la modalidad por comisión. Un QR pendiente no genera comisión. No hay tope comercial de volumen vendido del plan; permanecen los límites técnicos y bancarios.

Por defecto se cierra cada **7 días** y hay **24 horas** para pagar. Rigen las condiciones y fechas reales de cada comercio. Todo cierre con importe a liquidar exige pago, **sin mínimo comercial**. El siguiente ciclo sigue acumulando mientras se paga la factura anterior.

El proveedor puede incorporar la **barra de comisión y el panel de liquidación** de PagosYa, o construir su pantalla con la API. Diferenciar comisión del ciclo abierto de las facturas cerradas; mostrar saldo, vencimiento y confirmación.

La experiencia de liquidación puede ser **comercio**, **proveedor** o **ambos**. Define quién presenta y gestiona el pago; no transfiere la deuda al proveedor ni los fondos del comercio. El proveedor puede generar y compartir el enlace por sus propios canales, como correo o WhatsApp. Crear un enlace no hace que PagosYa envíe automáticamente esos mensajes.

Un enlace de liquidación fijado a una factura puede durar hasta **7 días**, sin ampliar el vencimiento de la deuda ni sus 24 horas de plazo. El QR de una venta cobra al comprador para el comercio; el de liquidación paga la comisión a PagosYa institucional.

## SaaS: dos bloqueos independientes

**Comisión vencida del comercio:** bloquea nuevos cobros QR **solo de ese comercio**. Los demás siguen habilitados si no tienen otras restricciones.

**Mensualidad o licencia vencida del proveedor:** bloquea nuevos cobros QR de **todos los afiliados**. Pagar la comisión de uno no renueva esa mensualidad.

**Ambas vencidas:** pagar una sola obligación no libera los cobros bloqueados por la otra. Deben estar habilitadas la licencia del proveedor y la situación del comercio, además de su banco conectado.

Los pagos anteriores siguen pudiendo confirmarse y la liquidación de deudas permanece disponible. El bloqueo no borra datos ni retiene dinero. Si ya pagó y no cambia el estado, consultar sin pedir otro pago y, si persiste, escalar a soporte@pagosya.com.bo.

## SaaS: sandbox y límites técnicos

Solicitar sandbox con el **formulario en la propia página** https://www.pagosya.com.bo/developers?producto=saas#solicitar. Tras la aprobación se entrega la clave por correo; no sustituir el formulario enviando al lead a escribir un e-mail.

Es el mismo sandbox de ventas de Checkout Web: QR ficticio no pagable, sin banco ni fondos. **No simula el SaaS completo**: no reproduce afiliación bancaria, comisiones, mensualidad o webhook global, ni reemplaza la clave global de plataforma. Esas operaciones requieren homologación controlada en producción con comercios autorizados. No enviar formularios ficticios al banco.

Límites SaaS: clave global hasta **120 solicitudes por minuto**, compartidas por sus comercios; los cobros también respetan el límite interno del comercio, **60/min por defecto**. Sesiones bancarias: hasta **120 aperturas por hora por proveedor**, vigencia 30 minutos. La capacidad de 10, 50 o 200 es de afiliados, no un tope mensual de bolivianos vendidos.

## SaaS: respuestas rápidas del atendente

**¿Cada afiliado compra otro plan o paga Bs. 49,90?** No: la activación está incluida en SaaS, sin otro login de PagosYa. El proveedor paga mensualidad y cada comercio su comisión.

**¿Quién elige 1% o 2%?** El administrador SaaS lo acuerda con el comercio: Embedded 1% o White Label 2%. El titular acepta las condiciones.

**¿Repito la integración para cada cliente?** No, se desarrolla globalmente una vez; se vinculan por separado los datos, el consentimiento y el banco de cada empresa.

**¿Dónde guarda las credenciales cuando las entregue el banco?** Vuelve al menú Integración bancaria de su SaaS; se abre una sesión nueva y su trámite anterior permanece guardado.
