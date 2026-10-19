---
title: "MercadoYa — cobro con QR y aviso por voz para puestos de mercado"
version: 1.0
audiencia: "merchants, agents, support"
actualizado_en: 2026-10-19
---

**MercadoYa** es el plan de PagosYa para **puestos de mercado, ferias y kioscos**. Hace una sola cosa y la hace rápido: el puesto pone un **QR fijo impreso**, el cliente lo escanea, escribe el monto en la app de su banco y paga, y **el celular del vendedor dice en voz alta** «Llegó 25 bolivianos de María Quispe». El pago ya viene confirmado por el banco: el vendedor no tiene que mirar comprobantes, sacar fotos ni entrar a su app bancaria.

Es el plan más económico de PagosYa: **Bs. 39,90 al mes**, sin comisión por venta y sin comprar ningún aparato (usa el celular Android del vendedor).

**Página del plan (mandá siempre este link):** https://www.pagosya.com.bo/mercadoya

---

## 🎯 ¿Qué resuelve?

En los mercados casi todos pagan con QR, y el fin de semana hay fila. Hoy el puesto valida el pago de tres maneras, las tres malas:

| Cómo se valida hoy | Problema | Con MercadoYa |
|---|---|---|
| El cliente muestra el comprobante en su celular | Pantalla chica, apuro, fila. Una captura se puede editar o volver a mostrar | El aviso sale solo cuando el banco confirma el pago |
| El vendedor le saca foto al comprobante | La galería se llena y la foto no prueba que la plata llegó | Cada pago queda registrado como cobro, con monto, hora y nombre de quien pagó |
| El dueño entra al banco a revisar el extracto | Deja de atender; el ayudante tiene que esperarlo | El celular del que cobró lo anuncia en voz alta en segundos |

---

## 📦 Plan y precio

| | MercadoYa |
|---|---|
| **Mensual** | **Bs. 39,90** |
| **Anual** | **Bs. 399** (se pagan 10 meses y se usan 12) |
| **Prueba gratis** | **7 días** |
| Puestos (tiendas) | 1 |
| Usuarios | El dueño + **2 ayudantes** (empleados) |
| Límite de cobros | **Bs. 40.000 / mes** (en la prueba: Bs. 15.000) |
| Comisión por venta | **0%** |
| Facturación SIAT | No incluye (pensado para rubro informal) |
| POS, productos, inventario, tienda online | No incluye |

Código técnico del plan: `MercadoYa_v1` (prueba: `trial_mercadoya`).

> ⚠️ Nunca prometas pago con **tarjeta**: MercadoYa (y PagosYa) cobra **solo con QR**.

### Prueba gratis de 7 días

MercadoYa es una de las **dos excepciones** a la regla «PagosYa no tiene prueba gratis» (la otra es Nia). La prueba:

- Se activa con el botón **«Probar 7 días gratis»** en https://www.pagosya.com.bo/mercadoya (o en la tarjeta MercadoYa de https://www.pagosya.com.bo/planes). El registro es el mismo de los demás planes.
- Trae la misma interfaz y las mismas funciones del plan pago, con límite de cobros de **Bs. 15.000** durante la prueba.
- **Una prueba por carnet (CI):** si el CI ya usó una prueba de PagosYa, no se puede activar otra.
- No pide tarjeta. Al terminar, el comerciante elige mensual o anual y paga con QR.

> La prueba gratis vale **solo para MercadoYa** (y para Nia). Si el lead pregunta por otro plan (EmprendeYa, ExpandeYa, ConquistaYa, RestauranteYa, CobraYa, Condominios, WhatsApp CRM, Checkout), **no hay prueba**: ofrecé videos en https://pagosya.com.bo/links o una demostración en vivo.

---

## 🏦 Bancos: requisito obligatorio

El QR fijo (el que se imprime y el cliente pone el monto) **solo existe hoy en dos bancos**:

- **BNB** (Banco Nacional de Bolivia)
- **Banco Económico (Baneco)**

El puesto necesita una **cuenta en uno de esos dos bancos** conectada a PagosYa. Con **Red Enlace** o **Banco Ganadero** el QR fijo no está disponible (el sistema muestra «El QR Fijo no está disponible con … Usa QR Variable»).

El cliente que paga puede usar **la app de cualquier banco**: el QR es interbancario. El requisito es solo de la cuenta del puesto.

El dinero llega **directo a la cuenta bancaria del comerciante**. PagosYa no toca la plata: solo confirma y registra el pago.

---

## 🔁 Cómo funciona (paso a paso)

1. **El vendedor genera su QR** en la app → pestaña **Mi QR** → «Generar mi QR». El banco se toma solo de la integración bancaria de la tienda.
2. **Imprime el cartel**: sale con el logo de PagosYa, el **nombre del puesto**, el **nombre de quien atiende** y la frase «Escanea, pon el monto y paga». Se puede **imprimir** (tamaño A5), **compartir por WhatsApp** o **descargar**.
3. **El cliente escanea** con la app de su banco, **escribe el monto** y paga.
4. **El banco confirma** el pago a PagosYa.
5. **El celular de quien generó ese QR habla**: «Llegó 25 bolivianos de María Quispe». Cada pago se guarda como un cobro (monto, hora, nombre del pagador, vendedor).

El QR fijo **sirve para muchos pagos** (no hay que generar uno por venta) y es válido por **1 año**. Generar uno nuevo reemplaza al anterior: hay que reimprimir el cartel.

---

## 👥 Dueño y ayudantes: cada uno con su QR

- **Cada usuario genera su propio QR** (el dueño y cada ayudante). El QR queda ligado al **puesto y a la persona** que lo generó.
- **El aviso de voz suena solo en el celular de quien generó el QR** que se usó. Si el cliente le paga al QR del ayudante, habla el celular del ayudante.
- **El ayudante ve solo lo suyo**: su QR, sus cobros y sus totales.
- **El dueño ve todo**: el total del puesto y **cuánto cobró cada ayudante**, más la barra de uso del límite mensual del plan.

Los ayudantes se crean desde **Más → Ayudantes** (máximo 2 en este plan). El dueño ve el detalle en **Más → Ventas por vendedor**. Cada uno entra con su propio usuario en la app.

---

## 🔊 El aviso por voz

La voz funciona en la **app Android de PagosYa** (versión 1.6.0 o superior), con la sesión iniciada en el celular del vendedor.

**Qué dice:** «Llegó [monto] bolivianos de [nombre]». Si el banco no envía el nombre del pagador, dice solo el monto.

**Configuración (pestaña Voz):**

| Opción | Qué hace |
|---|---|
| **Activar voz** | Prende o apaga los avisos en ese celular |
| **Tipo de voz** | Tres voces bien distintas: **Normal**, **Rápida** y **Grave y fuerte** (la más audible en un mercado con ruido) |
| **Decir el nombre de quien pagó** | Viene **activado**. Si se apaga, dice solo el monto |
| **Probar** | Reproduce un aviso de ejemplo |
| **Modo parlante** | Deja la pantalla encendida con brillo bajo mientras se atiende, para que el aviso salga al instante |
| **Batería** | Guía para quitar la «optimización de batería» de la app |

### ¿Cuánto tarda?

Medido con pagos reales (octubre 2026), desde que el banco confirma:

- **Con la pantalla encendida (modo parlante): 2 a 3 segundos.**
- Con la pantalla apagada, Android puede demorar el aviso **8 a 12 segundos** (ahorro de energía del sistema).

Por eso, para la venta del fin de semana recomendá **activar el Modo parlante** y quitar la optimización de batería. No prometas tiempos menores a esos.

> 🔋 En celulares Xiaomi, Huawei, Oppo, Vivo y similares, si no se quita la optimización de batería, el aviso puede no llegar con la app cerrada. La pestaña Voz guía el paso.

### Varios usuarios en el mismo celular

Si en un mismo celular se cierra la sesión del dueño y entra un ayudante (o al revés), **los avisos pasan a la cuenta que inició sesión**. No hace falta reinstalar nada.

---

## 📱 La app del plan

MercadoYa usa **la misma app y el mismo sitio de PagosYa**, con una interfaz propia y simple. El menú tiene cinco secciones:

| Sección | Qué hay |
|---|---|
| **Inicio** | Cobrado hoy, estado de la voz (activa/apagada) y gráficos con datos reales: cobros por hora (horas pico), últimos 7 días y ticket promedio. El dueño ve además la barra del límite mensual y los totales por ayudante |
| **Mi QR** | Generar el QR, ver el cartel, imprimir, compartir, descargar |
| **Cobros** | Lista de cobros (Hoy / Ayer / 7 días) con monto, hora y pagador, más el total y el ticket promedio. El dueño ve además qué ayudante cobró cada uno |
| **Voz** | Configuración del aviso (ver arriba) |
| **Más** | Ventas por vendedor, Ayudantes, Mi plan, Mi perfil, Soporte y demás ajustes |

No tiene caja registradora, POS, productos ni facturas.

---

## 🆚 MercadoYa frente a los «parlantes» que se compran

Hay aparatos que anuncian pagos por voz. Al comparar, usá solo **hechos de MercadoYa** y no nombres de otras empresas:

| | Aparato que se compra | MercadoYa |
|---|---|---|
| Equipo | Hay que comprarlo | Usa el celular del vendedor |
| Comisión | Suelen cobrar un % por cada venta | **0%**, nunca |
| Costo mensual | Sube mientras más se vende | **Bs. 39,90 fijo** |
| Ayudantes | Otro aparato por persona | **2 ayudantes incluidos**, cada uno con su QR |
| Si se pierde o se daña | Hay que comprar otro | Se instala la app de nuevo |

> ❌ No digas que un competidor «tarda X segundos» ni cites sus precios: no lo podemos comprobar. Hablá de lo nuestro.

**Ejemplo de cuenta:** un puesto que cobra Bs. 15.000 al mes con QR pagaría Bs. 150/mes con una comisión de 1%. Con MercadoYa paga Bs. 39,90.

---

## ⬆️ Cuándo ofrecer otro plan

| Si el comerciante necesita… | Ofrecé |
|---|---|
| Más de 2 ayudantes o más de Bs. 40.000/mes | **ExpandeYa** (3 tiendas, 3 empleados, Bs. 80.000/mes) |
| Productos, inventario o POS con carrito | **ExpandeYa** (Bs. 169) |
| Facturar con SIAT | **ExpandeYa** o superior |
| Tienda online | **ConquistaYa** |
| Banco Red Enlace o Ganadero (sin QR fijo) | Otro plan con **QR variable** (el QR se genera por venta, con el monto exacto) |

Al pasar a otro plan, el comerciante deja la interfaz MercadoYa y entra al panel completo de PagosYa.

---

## 💬 Cómo presentarlo (guion corto)

> «Con MercadoYa ponés un QR en tu puesto, el cliente paga desde su banco y **tu celular te dice en voz alta cuánto llegó y de quién**. Ya no tenés que mirar comprobantes. Son **Bs 39,90 al mes**, sin comisión y sin comprar aparato. Probalo **7 días gratis** acá 👉 https://www.pagosya.com.bo/mercadoya
> Solo necesitás cuenta en **BNB o Banco Económico**.»

Antes de mandar el link, **confirmá el banco**. Si el lead tiene Red Enlace o Ganadero, avisale que el QR fijo no está disponible con su banco.

---

## ❓ FAQ

**P: ¿Cuánto cuesta MercadoYa?**
R: Bs. 39,90 al mes o Bs. 399 al año (pagás 10 meses y usás 12). Sin comisión por venta.

**P: ¿Hay prueba gratis?**
R: Sí, 7 días, solo para MercadoYa. Se activa en https://www.pagosya.com.bo/mercadoya con «Probar 7 días gratis». Una prueba por carnet.

**P: ¿Con qué bancos funciona?**
R: El puesto necesita cuenta en BNB o Banco Económico. El cliente puede pagar desde cualquier banco.

**P: ¿Tengo que comprar algún aparato?**
R: No. Usás tu celular Android con la app de PagosYa.

**P: ¿Funciona en iPhone?**
R: El aviso por voz es de la app Android. En otros dispositivos se pueden ver los cobros, pero el aviso por voz necesita Android.

**P: ¿Cuánto tarda el aviso?**
R: Con la pantalla encendida (modo parlante), 2 a 3 segundos después de que el banco confirma. Con la pantalla apagada, Android puede demorarlo unos segundos más.

**P: ¿Mis ayudantes ven lo que cobro yo?**
R: No. Cada ayudante ve solo sus cobros. El dueño ve todo y lo que cobró cada uno.

**P: Si el cliente le paga al QR de mi ayudante, ¿suena en mi celular?**
R: No, suena en el celular del ayudante, que es quien está atendiendo. El dueño lo ve en Cobros.

**P: ¿El aviso dice el nombre del cliente?**
R: Sí, cuando el banco lo envía. Se puede apagar en la pestaña Voz para que diga solo el monto.

**P: ¿Puedo facturar?**
R: No, MercadoYa no incluye facturación SIAT. Para facturar, ExpandeYa o superior.

**P: ¿El QR vence?**
R: Es válido por un año y sirve para todos los pagos de ese período. Si generás uno nuevo, reimprimí el cartel.

**P: ¿Puedo cobrar con tarjeta?**
R: No. PagosYa cobra solo con QR.
