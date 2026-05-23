---
title: Configuración de impresoras térmicas
version: v1
audiencia: merchants
actualizado_en: 2026-05-23
---

# Configuración de impresoras térmicas

PagosYa soporta impresoras térmicas para imprimir **recibos de venta** y **tickets de producción** (cocina, bar, etc.). El comportamiento varía según si se usa la **app Android nativa** o la **versión web (navegador)**.

---

## Dónde configurar las impresoras

**Menú lateral → Configuraciones → Impresoras**

La pantalla de configuración se divide en:
- **Modo Restaurante** — activa el flujo de comandas y estaciones
- **Impresora de Recibos** — para el comprobante del cliente (solo app Android)
- **Estaciones de Producción** — para imprimir en cocina, bar u otras áreas (app Android y web)

---

## Versión App Android

### Paso 0 — Emparejar la impresora con el teléfono

Antes de configurar en PagosYa, la impresora debe estar **emparejada vía Bluetooth** con el dispositivo Android:

1. En el teléfono ir a **Ajustes → Bluetooth**.
2. Encender la impresora térmica.
3. Buscar dispositivos disponibles y seleccionar la impresora.
4. Confirmar el emparejamiento (si pide PIN, generalmente es `0000` o `1234`).
5. La impresora aparece como dispositivo vinculado en la lista de Bluetooth.

> Este paso se hace una sola vez por dispositivo. Una vez emparejada, PagosYa puede encontrarla automáticamente.

---

### Configurar la impresora de recibos (app Android)

La impresora de recibos se usa para imprimir el comprobante del cliente al finalizar una venta, y para los reportes de cierre de turno.

**Paso a paso:**

1. Ir a **Configuraciones → Impresoras**.
2. En la sección **"Impresora de Recibos"**, seleccionar el ancho del papel:
   - **58mm** — papel estrecho (más común en impresoras de bolsillo)
   - **80mm** — papel estándar de mostrador
3. Hacer clic en **"Buscar Bluetooth"**.
4. El sistema escanea durante 8 segundos los dispositivos Bluetooth disponibles.
5. Aparece la lista de impresoras encontradas.
6. Hacer clic en **"Usar en recibos"** junto a la impresora deseada.
7. Hacer clic en **"Probar"** para imprimir una hoja de prueba — verificar que el texto salga correctamente y que el ancho del papel coincida.
8. Hacer clic en **"Guardar recibos"** para guardar la configuración.

> La configuración se guarda localmente en el dispositivo. Si se cambia de teléfono, hay que volver a configurar.

**Qué imprime la impresora de recibos:**
- Comprobante de venta (al finalizar una venta en el POS)
- Reporte de cierre de turno de caja
- Comprobante de canje de cupones

---

### Configurar estaciones de producción vía Bluetooth (app Android)

Las estaciones de producción se usan para enviar pedidos a la cocina, bar u otras áreas de preparación. Requiere que el **Modo Restaurante** esté activado.

**Activar Modo Restaurante:**
1. En **Configuraciones → Impresoras**, activar el toggle **"Modo Restaurante"**.
2. Seleccionar el tipo de operación:
   - **Servicio en mesa** — usa comandas y envío a producción desde "Guardar pedido"
   - **Atención en caja** — flujo normal, permite enviar a producción después de cobrar

**Agregar una estación Bluetooth:**
1. En la sección **"Estaciones de Producción"**, completar:
   - **Nombre**: por ejemplo `Cocina`, `Bar`, `Cafetería`
   - **Tipo de conexión**: seleccionar `Bluetooth`
   - **Ancho del papel**: `58mm` o `80mm`
   - **Dirección Bluetooth**: hacer clic en **"Buscar Bluetooth"** para escanear y seleccionar la impresora, o ingresar manualmente la dirección MAC (formato `AA:BB:CC:DD:EE:FF`)
2. Hacer clic en **"Guardar estación"**.
3. Hacer clic en el ícono de **prueba** (⚡) para verificar la conexión — se imprimirá un ticket de prueba.

---

### Configurar estaciones de producción vía Wi-Fi / IP (app Android)

Útil para impresoras de red conectadas al router del local.

**Requisito:** la impresora y el teléfono deben estar en la **misma red Wi-Fi**.

**Cómo obtener la IP de la impresora:**
- La mayoría de impresoras térmicas de red imprimen su IP al encender manteniendo presionado el botón de avance de papel.
- También se puede consultar el panel de administración del router.

**Pasos:**
1. En la sección **"Estaciones de Producción"**, completar:
   - **Nombre**: por ejemplo `Cocina`
   - **Tipo de conexión**: seleccionar `Wi-Fi / IP`
   - **Ancho del papel**: `58mm` o `80mm`
   - **IP / Host**: la dirección IP de la impresora (ej: `192.168.1.120`)
   - **Puerto**: dejar `9100` (puerto estándar ESC/POS; cambiar solo si la impresora usa otro puerto)
2. Hacer clic en **"Guardar estación"**.
3. Hacer clic en el ícono de **prueba** (⚡) para verificar la conexión.

> Si la prueba falla, verificar que la IP sea correcta y que el dispositivo y la impresora estén en la misma red Wi-Fi.

---

## Versión Web (navegador)

En la versión web, **no es posible conectarse directamente a impresoras Bluetooth ni TCP/IP**. En cambio, el sistema usa el **diálogo de impresión del navegador** (`window.print()`), que envía el trabajo a cualquier impresora instalada en el sistema operativo del computador.

### Cómo funciona la impresión en web

- **Recibos de venta**: al hacer clic en "Imprimir" en el modal del recibo, se abre el diálogo de impresión del navegador (Chrome, Edge, etc.). El CSS incluye `@page { size: 58mm auto }` o `@page { size: 80mm auto }` según el ancho configurado.
- **Estaciones de producción**: el sistema abre una nueva ventana con el ticket formateado y la imprime automáticamente usando el diálogo del sistema.

---

### Paso 0 — Instalar el driver de la impresora en Windows

La impresora térmica debe estar instalada en Windows como impresora de sistema antes de poder usarla desde el navegador.

**Para impresoras USB o Bluetooth:**
1. Conectar la impresora al computador (USB) o emparejar vía Bluetooth.
2. Windows detecta automáticamente muchos modelos y descarga el driver.
3. Si no lo detecta, descargar el driver del sitio del fabricante (ej: Xprinter, Epson, Star, Bixolon) e instalarlo.
4. Verificar en **Panel de Control → Dispositivos e impresoras** que la impresora aparece.

**Para impresoras de red (Wi-Fi / IP):**
1. En **Panel de Control → Dispositivos e impresoras → Agregar una impresora**.
2. Seleccionar "La impresora que deseo no está en la lista".
3. Elegir "Agregar una impresora mediante una dirección TCP/IP o nombre de host".
4. Ingresar la IP de la impresora (ej: `192.168.1.120`) y puerto `9100`.
5. Seleccionar el driver correspondiente (usar "Generic / Text Only" si no hay driver específico).

---

### Paso 1 — Crear un tamaño de papel personalizado en Windows

El tamaño de papel estándar (A4, Carta) no coincide con el papel térmico. Hay que crear un tamaño personalizado:

1. Abrir **Panel de Control → Dispositivos e impresoras**.
2. Hacer clic derecho en la impresora térmica → **Preferencias de impresión**.
3. Buscar la opción **"Tamaños personalizados"** o **"Crear nuevo tamaño"** (depende del driver).
4. Crear un tamaño con:
   - **Nombre**: `Ticket 58mm` (o `Ticket 80mm`)
   - **Ancho**: `58mm` (o `80mm`)
   - **Alto**: `200mm` (o dejar en automático si el driver lo permite)
5. Guardar y establecer como tamaño predeterminado de la impresora.

> Si el driver no permite tamaños personalizados, usar el método alternativo desde Chrome (ver más abajo).

---

### Paso 2 — Configurar el ancho del papel en PagosYa (web)

PagosYa usa el ancho de papel guardado en la configuración para aplicar el CSS correcto al imprimir:

1. Ir a **Configuraciones → Impresoras**.
2. En la sección de Impresora de Recibos, seleccionar **58mm** o **80mm** según el papel de la impresora.
3. Esta preferencia se guarda localmente en el navegador y se aplica automáticamente al imprimir recibos.

---

### Paso 3 — Configurar el diálogo de impresión en Chrome / Edge

La primera vez que se imprime, configurar el diálogo de Chrome para obtener resultados correctos:

1. Al abrir el diálogo de impresión, hacer clic en **"Más ajustes"**.
2. Configurar:
   - **Impresora**: seleccionar la impresora térmica instalada
   - **Tamaño del papel**: seleccionar el tamaño personalizado creado (`Ticket 58mm` o `Ticket 80mm`)
   - **Márgenes**: `Ninguno` o `Mínimo`
   - **Escala**: `100%` (no ajustar al ancho de la página)
   - **Encabezados y pies de página**: desmarcar
3. Hacer clic en **"Imprimir"**.

> Chrome recuerda la última impresora usada por sitio web. Una vez configurado correctamente, las siguientes veces solo hay que hacer clic en "Imprimir".

---

### Configurar estaciones de producción en web

En la versión web, las estaciones de producción siempre usan el modo **"Navegador"** — abre una ventana con el ticket formateado y lanza el diálogo de impresión del sistema.

**Pasos:**
1. Activar **Modo Restaurante** en **Configuraciones → Impresoras**.
2. En la sección **"Estaciones de Producción"**, completar:
   - **Nombre**: `Cocina`, `Bar`, etc.
   - **Salida de impresión**: aparece fijo como *"Navegador / diálogo de impresión del sistema"*
   - **Ancho del papel**: `58mm` o `80mm`
3. Hacer clic en **"Guardar estación"**.
4. Hacer clic en el ícono de **prueba** (⚡) — se abre el diálogo de impresión del sistema.
5. Seleccionar la impresora y el tamaño de papel correcto.

---

## Tabla resumen: funciones por plataforma

| Función | App Android | Versión Web |
|---|---|---|
| Impresora de recibos vía Bluetooth | ✅ | ❌ |
| Impresora de recibos vía Wi-Fi/IP | ✅ | ❌ |
| Impresora de recibos vía diálogo del sistema | — | ✅ |
| Estación de producción vía Bluetooth | ✅ | ❌ |
| Estación de producción vía Wi-Fi/IP | ✅ | ❌ |
| Estación de producción vía diálogo del sistema | ✅ (opción browser) | ✅ |
| Selección de ancho de papel (58mm / 80mm) | ✅ | ✅ |
| Prueba de impresión | ✅ | ✅ |

---

## Solución de problemas comunes

**"No se encontraron impresoras Bluetooth"** (app Android)
- Verificar que el Bluetooth del teléfono está activado.
- Verificar que la impresora ya está emparejada en **Ajustes → Bluetooth** del teléfono.
- Reiniciar la impresora y repetir el escaneo.

**"No se pudo conectar a la impresora"** (app Android)
- La impresora puede haberse apagado o estar fuera de alcance.
- Verificar que la impresora está encendida y a menos de 10 metros del teléfono.
- Desemparejar y volver a emparejar la impresora desde los ajustes de Bluetooth del teléfono.

**El recibo sale en tamaño A4 o muy pequeño** (web)
- El tamaño de papel no está configurado correctamente en el diálogo de Chrome.
- Seguir el Paso 1 (crear tamaño personalizado) y el Paso 3 (configurar Chrome).
- Verificar que la preferencia de ancho de papel en PagosYa (58mm / 80mm) coincide con el papel real.

**El recibo sale cortado o le falta texto** (web)
- Reducir los márgenes en el diálogo de impresión a "Ninguno".
- Verificar que la escala está al 100% y no en "Ajustar al ancho de página".

**La ventana de impresión no se abre** (web)
- El navegador puede estar bloqueando las ventanas emergentes.
- En Chrome: hacer clic en el ícono de la barra de direcciones que indica "ventana emergente bloqueada" y permitir las ventanas emergentes de `pagosya.com.bo`.

**"Impresión TCP/IP solo está disponible en la app Android"** (web)
- En la versión web no es posible imprimir directamente por IP/TCP. Usar el modo navegador o usar la app Android para impresión directa por red.

---

## FAQ

**¿Puedo tener una impresora de recibos y varias estaciones de producción al mismo tiempo?**
Sí. La impresora de recibos es independiente de las estaciones. Se pueden configurar ambas simultáneamente.

**¿Cuántas estaciones de producción puedo crear?**
No hay límite. Se pueden crear tantas estaciones como sea necesario (Cocina, Bar, Cafetería, Pastelería, etc.).

**¿La configuración de impresoras se sincroniza entre dispositivos?**
No. La configuración de impresoras se guarda localmente en cada dispositivo. Si se usa PagosYa en dos teléfonos o computadores, hay que configurar las impresoras en cada uno por separado.

**¿Funciona con cualquier marca de impresora térmica?**
La app Android es compatible con impresoras que usan el protocolo **ESC/POS** vía Bluetooth o TCP/IP — la mayoría de impresoras térmicas del mercado (Xprinter, Epson TM, Star, Bixolon, Rongta, etc.). En la versión web, funciona con cualquier impresora instalada en Windows.

**¿El ancho del papel afecta el contenido impreso?**
Sí. El sistema adapta automáticamente el formato:
- **58mm**: máximo 30 caracteres por línea
- **80mm**: máximo 42 caracteres por línea

Los textos más largos se cortan o se reducen automáticamente para ajustarse al ancho del papel.