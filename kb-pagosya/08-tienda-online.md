---
title: Tienda online integrada
version: v6
audiencia: merchants
actualizado_en: 2026-10-07
---

# Tienda online integrada

La **Tienda Online** de PagosYa convierte tu negocio físico en una tienda digital lista para vender, cobrar por QR y recibir pedidos organizados. El catálogo se sincroniza automáticamente con el inventario del POS — cualquier cambio en precios, stock o productos del POS se refleja de inmediato en la tienda online.

> **Hosting y dominio incluidos:** El enlace `{subdominio}.pagosya.shop`, el hosting y todos los servicios de la tienda online están **100% incluidos en el plan**, sin costo adicional. No se necesita servidor propio, ni programadores, ni contratos externos.

**Capacidades principales:**
- Catálogo digital con hasta 5 fotos, 1 video corto, descripciones, variantes y stock en tiempo real
- **Inventario sincronizado en tiempo real** con la tienda física — una sola carga, dos canales de venta
- Cobro por QR automatizado con 0% de comisión (BANECO / BNB / Red Enlace / PIX)
- Pago con tarjeta de crédito/débito (si tiene integración Red Enlace 3DS activa)
- **Contra entrega**: el cliente paga al recibir, con QR en el acto o efectivo
- Pedidos organizados en panel de gestión, con **alerta sonoro de nuevo pedido** en el panel
- **Portal de seguimiento para el cliente** (`/mipedido`): sigue el estado de su pedido en tiempo real, sin cuenta ni contraseña
- **6 plantillas de diseño** listas para usar, todas adaptadas a celular y tablet
- **Plantilla de servicios con reservas en línea** (Barbería): el cliente reserva su turno dentro de la tienda, con horarios reales de la Agenda
- **Chat en la tienda**: los clientes chatean con tu bot y los mensajes llegan a la bandeja del WhatsApp CRM *(requiere WhatsApp CRM)*
- Personalización completa: plantilla, colores, tipografía, logo, banners, menú, contacto
- Entrega física (delivery/retiro) o entrega digital (email/WhatsApp)
- Enlace propio: `tutienda.pagosya.shop` o dominio personalizado
- **Hosting, subdominio y certificado SSL gratuitos** — incluidos en todos los planes

---

## Sección 1 — Crear una tienda online

### Acceso

Ir a **Tienda Online** desde el menú lateral del panel. Si no hay tiendas creadas, se ofrece la opción de crear la primera.

### Pasos para crear

1. Hacer clic en **"Nueva Tienda Online"**.
2. Completar el formulario de creación:

| Campo | Descripción |
|-------|-------------|
| **Tienda Física** *(obligatorio)* | Seleccionar la tienda del sistema a la que se vinculará esta tienda online (cada tienda física puede tener solo una tienda online) |
| **Nombre** | Nombre de la tienda online (se autorrellena como "Nombre de la tienda + Online") |
| **Descripción** | Texto de presentación de la tienda |
| **Subdominio** | Parte del enlace `{subdominio}.pagosya.shop` — **sin costo adicional** |
| **Dominio personalizado** | Si el negocio tiene su propio dominio (ej: `mitienda.com`) |
| **Estado** | Borrador (no visible al público) o Publicada (accesible online) |

3. Hacer clic en **"Crear"**.

> Cada tienda física puede tener únicamente **una tienda online**. Si ya tiene una, la opción aparece deshabilitada en el selector.

> El subdominio `{subdominio}.pagosya.shop` está disponible inmediatamente sin trámites de DNS. El **hosting, almacenamiento de imágenes y certificado SSL (HTTPS)** están incluidos en el plan.

---

## Sección 2 — Panel de tiendas online

Las tiendas creadas se muestran en **tarjetas** con:
- Nombre de la tienda online
- Badge de estado: **Publicada** (verde) o **Borrador** (gris)
- Nombre de la tienda física vinculada
- Descripción
- URL del subdominio

**Acciones disponibles por tarjeta:**

| Botón | Acción |
|-------|--------|
| **Editar** | Modificar nombre, descripción, subdominio o dominio personalizado |
| **Vista** (ícono de globo) | Ver la tienda tal como la ven los clientes (modo preview) |
| **Personalizar** (ícono de engranaje) | Abrir el Personalizador completo de la tienda |
| **Eliminar** (ícono de papelera) | Eliminar la tienda online permanentemente |

---

## Sección 3 — Personalizador de tienda

El **Personalizador** es el panel central de configuración de la tienda online. Se organiza en pestañas en la barra lateral: **Diseño**, **General**, **Banners**, **Menú**, **Contacto**, **Integraciones**, **Entrega** y **Preview**.

> El Personalizador siempre abre con la configuración guardada más reciente. Si el comercio dice que "un cambio se perdió", pedirle que cierre y vuelva a abrir el Personalizador y revise el campo: lo que se ve ahí es exactamente lo que está guardado.

---

### Pestaña 1: Diseño y plantilla

Define el aspecto general de la tienda. Cambiar la plantilla **conserva** productos, banners, menús, contactos y configuración de entrega.

**Plantillas disponibles:**

| Plantilla | Pensada para |
|---|---|
| **Clásico** | El diseño original de PagosYa. Ideal para mantener una tienda existente sin cambios. |
| **Modern Commerce** | Comercios en general. Presentación visual y editorial, enfocada en conversión. |
| **Restaurante & Delivery** | Restaurantes y cafeterías. Menú en lista, con resumen de pedido siempre visible. |
| **Infoproductos & Licencias** | Productos digitales: licencias, cursos, streaming y entrega por correo. |
| **Catálogo Mayorista** | Venta por volumen: catálogo con SKU, compra por caja y resumen comercial. |
| **Barbería** *(Agenda)* | Barberías y negocios de servicios: servicios, equipo y **reserva de turnos en línea** con los horarios reales de la Agenda. Incluye sección de tienda para vender productos. |

**Antes de elegir**, cada plantilla ofrece dos vistas previas:
- **Ver demostración**: muestra la plantilla con contenido de ejemplo.
- **Con mis productos**: muestra la plantilla con el catálogo real de la tienda.

En ambas se puede alternar entre **escritorio, tablet y celular** para ver cómo queda en cada dispositivo. Todas las plantillas son responsivas.

**Además, en esta pestaña se configura:**
- **Colores**: principal, acento, fondo, superficie y texto.
- **Tipografía**: fuente para títulos y para texto.

---

### Plantilla Barbería — reservas dentro de la tienda

Es la primera **plantilla de servicios**. Toda la página lleva al cliente a reservar: no necesita llamar ni escribir para pedir horario. Próximamente: médico, dentista, clínica y salón de belleza, con la misma lógica.

**Qué muestra (todo sale de la Agenda de Citas, no se carga dos veces):**
- **Portada** con el botón **"Reservar turno"** y una tarjeta **"Próximo turno libre"** con el primer horario real disponible.
- **Servicios** con precio y duración. Cada uno tiene su botón **Reservar**.
- **Equipo**: foto, cargo, descripción y próximo horario libre de cada profesional, con el botón **"Reservar con [nombre]"**.
- **Tienda**: los productos del catálogo (pomadas, aceites, etc.) con el mismo carrito y checkout de siempre. Solo aparece si la tienda tiene productos.
- **Horario de atención**, armado solo a partir de los horarios de la Agenda — si el comercio cambia la Agenda, la página se actualiza sola. Dirección con botón **"Cómo llegar"** (Google Maps).
- En el celular, una **barra fija abajo** con "Reservar turno" y WhatsApp.

**Cómo reserva el cliente:** toca Reservar → elige profesional (si hay uno solo, se salta) → servicio → horario → escribe nombre y WhatsApp → listo. Todo en una ventana dentro de la tienda, sin salir de la página. Es el mismo flujo del link de agenda `/agenda/...`, así que **nunca muestra un horario que no exista**.

**Sin portada propia:** si el comercio no sube un banner, la Barbería usa una imagen profesional de barbería ya incluida.

**Requisitos para que las reservas funcionen:**
1. Plan **WhatsApp CRM** activo (la Agenda es parte del CRM).
2. En **Agenda**: profesionales cargados, con horario y con **enlace público activo**. Los servicios son opcionales (sin servicios, se usa la duración por defecto).

**Sin WhatsApp CRM** la plantilla igual se puede usar: muestra el equipo y los servicios, pero los botones pasan a **"Reservar por WhatsApp"** (abre un mensaje ya escrito, ej.: "Hola, quiero reservar Corte + barba con Mateo"). Al dueño, y solo a él, le aparece un aviso de que las reservas en línea necesitan el WhatsApp CRM, con el botón **Ver planes**.

**¿A qué agenda llegan las reservas?** A la Agenda de la **tienda a la que pertenece esa tienda online**. Si el comercio tiene varias tiendas, en la vista previa el dueño ve el aviso *"Las reservas de esta tienda online entran en la agenda de [tienda]"* con el botón **Ver agenda**, que abre la Agenda correcta. Si esa tienda no tiene WhatsApp conectado, el aviso lo dice: la cita entra igual, pero **sin recordatorio** por WhatsApp.

> **Si el cliente dice "hice una reserva y no aparece en la agenda":** casi siempre está mirando la Agenda de otra tienda. En la Agenda, cambiar el selector de tienda (arriba, al lado del título) a la tienda de la tienda online.

**Medición:** cada reserva confirmada envía el evento **Schedule** al Meta Pixel y un evento a Google Analytics, si están configurados en Integraciones.

---

### Pestaña 2: General

Configuración básica de apariencia y comportamiento:

- **Logo**: subir una imagen de logo (máximo 2MB). Se muestra en la cabecera de la tienda. Botón para eliminar el logo actual.
- **Pago contra entrega**: activar o desactivar la opción de que los clientes elijan pagar al recibir el pedido.

> Si "Pago contra entrega" está activado, aparecerá como opción de pago en el checkout de la tienda. Si está desactivado, los clientes solo podrán pagar por QR, PIX o tarjeta.

---

### Pestaña 3: Banners

Los banners son las imágenes destacadas que aparecen en la parte superior de la tienda online, en formato carrusel.

**Por cada banner se puede configurar:**
- **Título**: texto principal del banner
- **Subtítulo**: texto secundario
- **Descripción**: texto de apoyo
- **Imagen**: subir imagen desde archivo (se sube al almacenamiento de PagosYa)
- **Enlace**: URL destino al hacer clic en el banner
- **Categoría**: enlace rápido a una categoría del catálogo
- **Texto del botón**: etiqueta del botón (ej: "Ver Ofertas")
- **Tarjeta de texto sobre el banner**: mostrar u ocultar el título, subtítulo y descripción encima de la imagen. **Desactivar cuando la imagen ya trae su propio texto/diseño.**
- **Usar botón**: mostrar u ocultar el botón de acción
- **Activo**: activar o desactivar el banner sin eliminarlo
- **Orden**: subir o bajar el banner en el carrusel

**Acciones:**
- **Agregar banner**: crea un nuevo banner editable
- **Eliminar banner**: elimina el banner seleccionado
- **Subir / Bajar**: reordena los banners en el carrusel

> El carrusel rota automáticamente cada 5 segundos si hay más de un banner activo.

**Tamaño de imagen recomendado (varía según la plantilla):**

| Plantilla | Medida | Proporción |
|---|---|---|
| Clásico | 1200 × 400 px | 3:1 |
| Modern Commerce | 1600 × 800 px | 2:1 |
| Restaurante & Delivery | 1600 × 900 px | 16:9 |
| Infoproductos & Licencias | 1600 × 900 px | 16:9 |
| Catálogo Mayorista | 1600 × 900 px | 16:9 |
| Barbería | 1600 × 900 px | 16:9 |

La pestaña Banners muestra siempre la medida correcta de la plantilla activa. Como cada portada recorta la imagen de forma distinta, conviene dejar el texto y los elementos importantes hacia el centro.

> **Banner con imagen que ya trae texto (arte lista):** desactivar **"Tarjeta de texto sobre el banner"** y, si la imagen no necesita botón, **"Usar botón"**. Así la portada muestra solo la imagen, sin textos ni botón encima. Funciona en Clásico, Modern Commerce, Restaurante y Barbería. En la Barbería, además, la imagen se muestra **entera en tablet y celular** (sin recortar el texto) y los botones de reserva pasan a una franja debajo de la imagen.
>
> En el celular, una imagen horizontal queda chica. Si el texto de la imagen es pequeño, conviene una arte con letras grandes.

---

### Pestaña 4: Menú

Configura la barra de navegación de la tienda online.

**Por cada ítem de menú se puede configurar:**
- **Nombre**: texto visible en la barra de navegación
- **Tipo**:
  - `Página`: enlace a una sección interna (ej: `#home`, `#productos`, `#contacto`)
  - `Categoría`: enlace a una categoría del catálogo (`#categoria/{id}`)
  - `Personalizado`: cualquier URL
- **URL**: destino del enlace
- **Visible**: mostrar u ocultar el ítem sin eliminarlo
- **Orden**: reordenar los ítems del menú

**Acciones:**
- Agregar, editar, eliminar y reordenar ítems de menú

---

### Pestaña 5: Contacto

Configura los datos de contacto que aparecen en el pie de la tienda online:

- **WhatsApp**: número de contacto (se usa también para el botón de contacto flotante y notificaciones de pedidos)
- **Teléfono**: número de teléfono adicional
- **Email**: correo electrónico de contacto
- **Facebook**: enlace al perfil
- **Instagram**: enlace al perfil
- **Twitter**: enlace al perfil

Los íconos de redes sociales aparecen automáticamente al cargar el campo correspondiente.

---

### Pestaña 6: Integraciones

Conecta la tienda con herramientas de analítica y remarketing:

| Integración | Campo | Para qué sirve |
|-------------|-------|----------------|
| **Meta Pixel** | ID del Pixel | Rastreo de eventos en Facebook / Instagram Ads |
| **Google Analytics** | ID de GA4 | Métricas de tráfico y conversión en Google Analytics |
| **TikTok Pixel** | ID del Pixel | Rastreo de eventos para TikTok Ads |

Ingresar el ID correspondiente de cada plataforma. Los eventos de vista de producto, agregar al carrito y compra se registran automáticamente.

#### Chat en tu tienda *(requiere WhatsApp CRM)*

Agrega un **botón de chat** en la esquina inferior izquierda de la tienda online, en todas las plantillas.

- El cliente escribe su **nombre** y, si quiere, su **WhatsApp**, y empieza a chatear.
- Responde el **mismo chatbot del WhatsApp CRM** (reglas, IA, agenda, horario de atención). No hay que configurar nada aparte.
- Las conversaciones llegan a la **bandeja del WhatsApp CRM** con el canal **Web** (ícono de globo violeta), junto con WhatsApp e Instagram. El equipo responde desde ahí y la respuesta aparece en el chat de la tienda en segundos.
- **Mensaje de bienvenida** opcional (máx. 200 caracteres). Si se deja vacío: "¡Hola! Bienvenido a [tienda]. ¿En qué te podemos ayudar?".
- Los links que manda el bot (agenda, pago) se pueden tocar en el chat.

**Cómo activarlo:** Personalizar Tienda → Integraciones → **Chat en tu tienda** → activar → **Guardar Todo**.

**Sin WhatsApp CRM:** la opción se ve (con el sello 🔒 WhatsApp CRM), pero al intentar activarla aparece el aviso *"El chat de la tienda es parte del WhatsApp CRM"* con el botón **Comprar WhatsApp CRM**.

**Cosas a saber:**
- Los mensajes llegan a la bandeja de la tienda **donde está conectado el WhatsApp** del dueño (si la tienda de la tienda online no tiene WhatsApp propio).
- Si el chatbot está apagado, los mensajes igual llegan a la bandeja para responder a mano.
- Si el cliente cierra la página, la respuesta queda guardada y la ve cuando vuelve a la tienda (en el mismo navegador). Por eso se le pide el WhatsApp: en la conversación aparece el número para seguir por WhatsApp.
- Hay límite anti-spam: un cliente no puede mandar más de 10 mensajes por minuto.

---

### Pestaña 7: Entrega

Configura el modo y opciones de entrega disponibles para los clientes:

**Modo de entrega:**
- **Física**: el cliente elige entre delivery o retiro en tienda
- **Digital**: el cliente recibe el producto por email o WhatsApp
- **Ambas**: el cliente puede elegir entrega física o digital

**Opciones de entrega digital** (si está habilitada):
- Email: el merchant entrega el producto digital por correo
- WhatsApp: el merchant entrega el producto digital por WhatsApp

**Textos personalizables:**
- Título de la sección de entrega (ej: "Forma de Entrega")
- Texto de ayuda (ej: "Recibirás tu producto después de confirmar el pago")
- Etiqueta y descripción del campo de email
- Etiqueta y descripción del campo de WhatsApp

> La pestaña Entrega es especialmente útil para negocios que venden **productos digitales**: cursos, vouchers, licencias, archivos descargables.

---

### Vista previa (Preview) y Editor visual

La pestaña **Preview** guarda los cambios y abre la tienda en el **Editor visual**, que muestra cómo verán los clientes la tienda. También es accesible desde el botón de globo en la tarjeta de cada tienda.

**Barra superior del Editor visual:**

| Botón | Qué hace |
|---|---|
| **Salir** | Vuelve al panel de tiendas online |
| **Editar diseño** | Modo edición: al hacer clic en un texto o sección de la tienda se edita en el panel lateral (textos, visibilidad y espaciado de secciones, colores, tipografía) |
| **Probar como cliente** | Muestra la tienda **funcionando como la publicada**: se puede agregar al carrito, reservar turnos y usar el chat. Para volver a editar, tocar **Editar diseño** |
| Escritorio / Tablet / Celular | Cambia el tamaño de la vista |
| **Guardar borrador** | Guarda el diseño sin publicarlo |
| **Publicar** | Publica **el diseño** (textos y estilos del editor) |

> ⚠️ **"Probar como cliente" es real:** las reservas y pedidos que se hagan ahí entran de verdad en la Agenda y en Pedidos. Después de probar, cancelar la cita de prueba en Agenda.
>
> ⚠️ **"Publicar" del editor no publica la tienda.** Solo publica el diseño. Para que la tienda esté abierta al público, el estado de la tienda debe ser **Publicada** (formulario de edición de la tienda).

---

## Sección 4 — Catálogo de productos

### Sincronización con la tienda física

Los productos de la tienda online provienen **directamente del inventario del POS**. No hay una carga separada — cualquier cambio en el inventario físico se refleja automáticamente en la tienda online:

| Cambio en el POS | Efecto inmediato en la tienda online |
|-----------------|--------------------------------------|
| Activar / desactivar un producto | Aparece o desaparece del catálogo |
| Cambiar precio | El precio se actualiza al instante |
| Modificar descripción o nombre | Se actualiza automáticamente |
| Stock llega a 0 | El producto no se puede agregar al carrito |
| Stock repuesto | El producto vuelve a estar disponible |

Para que un producto aparezca en la tienda online:
- El producto debe estar **activo** en el inventario.
- Debe tener **precio** asignado.
- Opcionalmente: fotos, video, descripción y categoría.

### Imágenes y video por producto

Cada producto puede presentarse con **contenido multimedia completo**:

- **Hasta 5 imágenes**: el cliente las navega en la galería de detalle del producto. Se recomienda incluir: foto principal, detalles, variantes, empaque y contexto de uso.
- **1 video corto**: se muestra en la galería junto a las imágenes. Ideal para demostrar el uso del producto o destacar características.

> Las imágenes y el video se cargan desde el módulo de inventario del POS (sección de detalle del producto). Una sola carga sirve para el POS y para la tienda online.

**Funcionalidades del catálogo en la tienda pública:**
- Grid de productos (12 por página) con paginación
- **Búsqueda** en tiempo real por nombre de producto
- **Filtro por categoría** desde el menú de navegación
- **Stock en tiempo real**: si un producto se agota, no se puede agregar al carrito
- **Galería multimedia**: hasta 5 imágenes + 1 video corto por producto
- **Variantes**: si el producto tiene variantes (talla, color, etc.), el cliente las selecciona antes de agregar al carrito

---

## Sección 5 — Experiencia del cliente en la tienda

### Navegación y carrito

1. El cliente accede a la tienda por el enlace `{subdominio}.pagosya.shop` o el dominio personalizado.
2. Ve el banner con carrusel, el menú de navegación y el catálogo de productos.
3. Hace clic en un producto para ver el detalle: galería (fotos + video), descripción, precio, variantes.
4. Agrega productos al carrito (el carrito se guarda en el navegador).
5. Abre el carrito y hace clic en **"Proceder al pago"**.

### Formulario de checkout

El cliente completa:
- **Nombre** *(obligatorio)*
- **Email** *(obligatorio)*
- **Teléfono**
- **NIT** (para factura fiscal — si aplica)

**Forma de entrega** (según configuración del merchant):
- **Delivery**: ingresa dirección, ciudad, zona, referencia. Puede usar el botón GPS para autocompletar la dirección desde su ubicación.
- **Retiro en tienda**: no requiere dirección.
- **Email digital**: ingresa su correo para recibir el producto.
- **WhatsApp digital**: ingresa su número para recibir el producto.

### Métodos de pago y integración bancaria

PagosYa integra directamente con los principales sistemas de cobro de Bolivia y Brasil. El checkout es **completamente automatizado** — no hay transferencias manuales ni confirmaciones por WhatsApp:

#### QR Bolivia — BANECO / BNB / Red Enlace *(recomendado)*

1. El cliente selecciona "QR Bolivia" y hace clic en "Generar Código QR".
2. El sistema genera un **QR de cobro en tiempo real** usando la integración bancaria que el comercio tenga configurada (**BANECO**, **BNB** o **Red Enlace**). El comercio no elige en el checkout: PagosYa enruta automáticamente según su integración activa.
3. El cliente escanea el QR con su app bancaria (cualquier banco boliviano).
4. El pago se confirma **automáticamente en segundos** — sin intervención manual.
5. El pedido pasa a estado "Pagado" y el comercio recibe el **alerta de nuevo pedido** en su panel.

> Esta integración usa la red interbancaria boliviana. Cualquier banco (BNB, BANECO, Banco Mercantil Santa Cruz, Banco Unión, Bisa, etc.) puede escanear el QR sin comisión adicional.

#### QR PIX — Brasil

Disponible si el merchant tiene integración PIX activa. Mismo flujo que QR Bolivia pero en reales brasileños.

#### Tarjeta de crédito/débito — Red Enlace 3DS

Disponible si el merchant tiene activa la integración con Red Enlace. El cliente ingresa los datos de la tarjeta y el pago pasa por autenticación 3D Secure. El monto se acredita directamente en la cuenta bancaria del negocio.

#### Contra entrega — Pagar al recibir

Disponible si el merchant activó la opción en la **Pestaña General** del Personalizador.

**Cómo funciona para el cliente:**
1. El cliente selecciona "Contra entrega" en el checkout.
2. El pedido se registra con estado "Pendiente de pago".
3. El cliente recibe el pedido en su domicilio.
4. En el momento de la entrega, paga al repartidor.

**Cómo funciona para el merchant (al momento de entregar):**
- Opción A — **Cobrar con QR**: el repartidor abre el pedido en el panel, hace clic en "Cobrar con QR", y muestra el código al cliente. El cliente escanea y el pago se confirma en tiempo real. El pedido pasa automáticamente a "Entregado".
- Opción B — **Marcar como pagado**: para pagos en efectivo, el repartidor confirma el cobro manualmente y el pedido se cierra.

> La contra entrega es ideal para clientes que no tienen app bancaria o prefieren pagar en efectivo. Se recomienda configurar también un método de cobro QR como alternativa al efectivo.

### Confirmación del pedido

Tras el pago confirmado:
- Se muestra una pantalla de **confirmación con el número de pedido**.
- El carrito se vacía automáticamente.
- El cliente puede pulsar **"Contactar por WhatsApp"** para enviarle al comercio un mensaje ya redactado con los productos, el total, la forma de entrega y el estado del pago. Es el cliente quien decide enviarlo — no es un envío automático.
- En el panel del comercio se abre un **alerta de nuevo pedido** (ver abajo).

> En los pagos con QR el mensaje de WhatsApp incluye los productos y el total, pero no el número de pedido: la venta se numera después de confirmarse el pago. El número sí aparece en la pantalla de confirmación, en el alerta de nuevo pedido y en la lista de pedidos.

### Alerta de nuevo pedido (panel del comercio)

Cuando entra un pedido de la tienda online (pagado por QR o contra entrega), el panel muestra un **modal de alerta con sonido**, similar al de las apps de delivery:

- Suena un aviso que **se repite cada 2,5 segundos** hasta que se cierre el modal (se descarta solo a los 90 segundos).
- Muestra número de pedido, cliente y teléfono, productos, forma de entrega, estado del pago y total.
- El botón **"Ver pedido"** abre ese pedido directamente en la lista de pedidos.

**Requisitos para que suene:**
- Hay que tener el panel de PagosYa **abierto y con sesión iniciada** como dueño o empleado del comercio.
- El navegador debe permitir el audio de la página. Algunos navegadores bloquean el sonido hasta que se hace clic en algún lugar de la pestaña; si el modal aparece pero no suena, basta con interactuar una vez con la página.

---

## Sección 6 — Gestión de pedidos

### Acceso

Desde el menú lateral hacer clic en **"Pedidos"** (o la sección de pedidos de la tienda online).

### Pestañas de estado

| Pestaña | Qué muestra |
|---------|-------------|
| **Pendientes** | Pedidos pagados, no enviados |
| **Enviados** | Pedidos marcados como enviados |
| **Entregados** | Pedidos completados y entregados |
| **Cancelados** | Pedidos cancelados |

### Datos de cada pedido

- Número de pedido
- Nombre y teléfono del cliente
- Lista de productos (nombre, cantidad, precio)
- Total
- Método de pago
- Forma de entrega (delivery/retiro/digital)
- Dirección de entrega (si eligió delivery, con coordenadas GPS si el cliente las compartió)
- Estado del pago y del envío
- Fecha del pedido

### Acciones sobre un pedido

| Acción | Descripción |
|--------|-------------|
| **Marcar como enviado** | Cambia el estado a "enviado" |
| **Marcar como entregado** | Cambia el estado a "entregado" y completa el pedido |
| **Cancelar pedido** | Cancela el pedido |
| **Contactar por WhatsApp** | Abre WhatsApp con un mensaje pre-cargado al cliente (incluye número de pedido, productos y total) |
| **Cobrar con QR** | Para pedidos contra entrega: genera un QR de cobro en el momento de la entrega. El pago se confirma en tiempo real. |
| **Marcar como pagado** | Para pedidos contra entrega: marca manualmente como pagado en efectivo |

### Filtros y búsqueda

- **Búsqueda**: por nombre del cliente o número de pedido
- **Rango de fechas**: filtrar pedidos por período
- **Exportar CSV**: descarga todos los pedidos del filtro activo

### Pedidos contra entrega

Los pedidos con método de pago "contra entrega" tienen un indicador especial. Al momento de la entrega, el merchant puede:
1. Hacer clic en **"Cobrar con QR"**: genera un QR para que el cliente pague en el acto. El sistema detecta el pago en tiempo real.
2. O hacer clic en **"Marcar como pagado"**: para pagos en efectivo sin QR.

### Portal de seguimiento del pedido (para el cliente)

El cliente final tiene una página pública para **seguir su pedido en tiempo real**, sin crear cuenta ni contraseña: solo con el número de pedido.

**Dónde está:** en la misma dirección de la tienda, agregando `/mipedido` (también funciona `/seguimiento`):
- `tutienda.pagosya.shop/mipedido?orden=00049`
- en el dominio personalizado de la tienda, igual (`mitienda.com/mipedido`)
- si el cliente entra sin número, la página le pide ingresarlo (ej.: `00049` o `#00049`) y pulsa **Rastrear**

**Qué ve el cliente:**
- Número de orden y fecha, con el nombre y teléfono de la tienda
- Un avance de **4 pasos**: **Confirmado → En preparación → En camino** (o **Listo para retiro**, si eligió retirar en la tienda) **→ Entregado**, con un mensaje que explica el paso actual. Si el pedido se canceló, lo indica.
- Datos de entrega (dirección o local de retiro) y del pago: método, **Pagado** o **Pendiente de pago**, y total
- Resumen de productos con cantidades y precios
- Botón **"Contactar a la Tienda por WhatsApp"** con el número de pedido ya escrito

La página **se actualiza sola**: cuando el comercio cambia el estado del pedido en el panel, el cliente lo ve sin recargar.

**Cómo le llega el enlace al cliente** (lo envía el comercio desde el panel):
- En el **alerta de nuevo pedido**, el botón **"📲 Notificar por WhatsApp"** le manda al cliente un mensaje de agradecimiento con el enlace de seguimiento.
- Al **cambiar el estado** de un pedido (en preparación, enviado o listo para retiro, entregado), el panel ofrece enviar al cliente un mensaje de WhatsApp con el nuevo estado y el enlace; el mensaje se puede editar antes de enviarlo.
- Si el comercio tiene el **WhatsApp CRM conectado**, el mensaje sale por su número directamente. Si no, se abre WhatsApp con el mensaje listo para enviar.

> Los pasos "En preparación" y "En camino / Listo para retiro" solo avanzan si el comercio actualiza el estado del pedido en el panel. Si el comercio no lo actualiza, el cliente sigue viendo "Confirmado".

---

## Sección 7 — Dominio personalizado

Si el negocio tiene su propio dominio (ej: `mitienda.com`), puede vincularlo a la tienda online:

1. En el formulario de edición de la tienda, ingresar el dominio personalizado.
2. Configurar el DNS del dominio apuntando a los servidores de PagosYa (instrucciones disponibles en el panel).
3. El sistema verifica el dominio automáticamente. El estado cambia de **"Pendiente"** a **"Verificado"**.
4. Una vez verificado, la tienda es accesible también por el dominio personalizado.

> El subdominio `{subdominio}.pagosya.shop` siempre está disponible sin configuración adicional. El dominio personalizado es **opcional** y está disponible en todos los planes sin costo extra de PagosYa.

---

## Preguntas frecuentes

**¿Los productos del POS aparecen automáticamente en la tienda online?**

Sí. Todos los productos activos con precio aparecen en el catálogo online. El stock, los precios y las fotos se sincronizan automáticamente — no es necesario cargar los productos dos veces.

**¿Cuántas fotos y videos puedo agregar a cada producto?**

Hasta **5 imágenes** y **1 video corto** por producto. Se cargan desde el módulo de inventario del POS y aparecen automáticamente en la galería de la tienda online.

**¿La tienda online tiene costo adicional?**

No. El hosting, el enlace `{subdominio}.pagosya.shop`, el certificado SSL (HTTPS), el almacenamiento de imágenes y el procesamiento de pagos QR están **incluidos en el plan** sin costo adicional. Tampoco hay comisión sobre las ventas online.

**¿Cómo funciona el cobro por QR en la tienda online?**

La integración bancaria (BNB / Red Enlace / PIX) genera el QR automáticamente al finalizar el checkout. El cliente escanea con su app bancaria y el pago se confirma en segundos sin intervención manual. El negocio no necesita monitorear manualmente los pagos.

**¿Puedo tener más de una tienda online?**

Se puede crear una tienda online por cada tienda física registrada en el sistema. Si el negocio tiene 3 tiendas físicas, puede tener 3 tiendas online independientes.

**¿Qué pasa si un producto se agota mientras el cliente navega?**

El stock se verifica en tiempo real. Si un producto se agota, no puede agregarse al carrito. Si ya estaba en el carrito y el stock cambia antes de pagar, el sistema lo informa al cliente.

**¿Los pedidos online aparecen en los reportes?**

Sí. Las ventas de la tienda online aparecen en los Reportes de Ventas con canal "Tienda Online", en el historial de Cupones y en el reporte de Ventas por Funcionarios (si hay empleado asignado).

**¿Puedo publicar o despublicar la tienda online cuando quiera?**

Sí. Desde el formulario de edición de la tienda, el toggle de "Publicada / Borrador" permite activar o desactivar el acceso público en cualquier momento sin perder ninguna configuración.

**¿Puedo recibir reservas de turnos desde la tienda online?**

Sí, con la plantilla **Barbería** y el plan **WhatsApp CRM**. El cliente reserva dentro de la tienda con los horarios reales de la Agenda. Sin el CRM, la plantilla funciona pero las reservas se piden por WhatsApp.

**Hice una reserva de prueba y no aparece en la Agenda.**

La reserva entra en la Agenda de la tienda a la que pertenece la tienda online. Si el comercio tiene varias tiendas, cambiar el selector de tienda en la Agenda. En la vista previa de la Barbería, el botón **Ver agenda** abre directamente la Agenda correcta.

**El nombre que aparece al reservar no es de ningún profesional que conozco.**

Son los profesionales de la Agenda **de esa tienda**. Cada tienda tiene sus propios profesionales, servicios y citas.

**Subí un banner con texto en la imagen y encima aparecen otros textos y un botón.**

En Banners, desactivar **"Tarjeta de texto sobre el banner"** y **"Usar botón"**, y guardar.

**Activé el chat en la tienda pero no aparece.**

1. Confirmar que se tocó **Guardar Todo** después de activar, y que al reabrir el Personalizador sigue activado.
2. El chat no aparece en el modo **Editar diseño**: usar **Probar como cliente** o abrir la tienda publicada.
3. El dueño necesita el plan **WhatsApp CRM** activo.

**Los mensajes del chat de la tienda no llegan a la bandeja.**

Llegan a la bandeja del WhatsApp CRM con el filtro **Web**. Si el bot no responde, revisar que el **chatbot esté encendido** en el WhatsApp CRM — es la misma configuración que en WhatsApp.

**¿Los clientes de la tienda online se agregan a la base de clientes?**

Sí. Cada pedido realizado online registra al cliente en el módulo de Clientes del negocio, acumulando el historial de compras y el total gastado.
