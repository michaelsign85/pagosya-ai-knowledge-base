---
title: Créditos y ampliación de límites
version: v3
audiencia: merchants
actualizado_en: 2026-05-23
---

# Créditos y ampliación de límites

Los **créditos PagosYa** permiten ampliar el alcance del plan activo sin necesidad de cambiar de paquete ni esperar el próximo ciclo de facturación. Son la herramienta de flexibilidad para negocios en crecimiento.

**Resumen rápido:**
- 1 crédito = **Bs. 20**
- Se pueden comprar desde la pantalla de **Suscripción**, pagando por QR en segundos
- Se aplican con un clic, inmediatamente
- Dos usos posibles: **aumentar el límite de ventas** (permanente) o **agregar tiendas + empleados** (30 días)

---

## Sección 1 — Pantalla de Suscripción

### Acceso

Desde el menú lateral del panel ir a **"Suscripción"**.

### Qué muestra la pantalla

La pantalla de Suscripción tiene tres secciones principales:

**1. Estado del plan actual**
- Nombre del plan activo (ej: EmprendeYa, ExpandeYa, ConquistaYa...)
- Fecha de inicio y fecha de vencimiento
- Precio mensual o anual según el ciclo activo
- Límite de ventas mensual base (del plan) + extra acumulado por créditos
- Tiendas y empleados incluidos en el plan

**2. Créditos**
- Créditos disponibles (comprados pero no usados)
- Créditos usados en el ciclo actual
- Botón **"Comprar Créditos"**
- Botón **"Usar Créditos"** (si hay créditos disponibles)

**3. Cambiar de plan**
- Listado de planes disponibles con sus características
- Toggle para ver precios mensuales o anuales
- Botón de upgrade/downgrade para cambiar de plan

---

## Sección 2 — Planes disponibles

PagosYa ofrece cinco planes comerciales. Los créditos son complementarios a cualquier plan.

| Plan | Precio/mes | Precio/año | Límite ventas | Tiendas | Empleados |
|------|-----------|-----------|---------------|---------|-----------|
| **EmprendeYa** | Bs. 79 | Bs. 790 | Bs. 40,000/mes | 1 | 1 |
| **ExpandeYa** | Bs. 169 | Bs. 1,690 | Bs. 80,000/mes | 3 | 3 |
| **ConquistaYa** | Bs. 249 | Bs. 2,490 | Bs. 150,000/mes | 6 | 6 |
| **Plan Checkout Web** | Bs. 249 | Bs. 2,490 | Bs. 150,000/mes | 1 | 1 |
| **RestauranteYa** | Bs. 329 | Bs. 3,290 | Bs. 150,000/mes | 6 | 6 |

> El plan **anual** equivale a 10 meses de precio mensual — equivale a 2 meses gratis.

---

## Sección 3 — Comprar créditos

### Pasos para comprar

1. En la pantalla de Suscripción, hacer clic en **"Comprar Créditos"**.
2. Se abre el modal **"Comprar Créditos Adicionales"**.
3. Ingresar la **cantidad de créditos** a comprar (mínimo 1).
4. El modal muestra en tiempo real:
   - **Total a Pagar**: `cantidad × Bs. 20`
   - **Aumento de Límite**: `cantidad × Bs. 5,000`
5. Hacer clic en **"Comprar Crédito"**.
6. Se abre la pantalla de pago con **QR de cobro** (BNB / Red Enlace).
7. Escanear el QR con la app bancaria.
8. El pago se detecta automáticamente — los créditos se aplican en segundos.
9. El modal se cierra solo y el balance de créditos se actualiza.

> El pago de créditos usa el mismo sistema QR automatizado que el POS — sin intervención manual, sin confirmaciones por WhatsApp.

### Cálculo de ejemplo

| Créditos | Costo total | Aumento de límite |
|----------|-------------|-------------------|
| 1 | Bs. 20 | +Bs. 5,000 |
| 3 | Bs. 60 | +Bs. 15,000 |
| 5 | Bs. 100 | +Bs. 25,000 |
| 10 | Bs. 200 | +Bs. 50,000 |

---

## Sección 4 — Usar créditos

Una vez comprados, los créditos deben **aplicarse** eligiendo para qué se usarán.

### Pasos para usar

1. En la pantalla de Suscripción, hacer clic en **"Usar Créditos"**.
2. Se abre el selector **"¿Cómo quieres usar tus créditos?"**
3. Elegir entre las dos opciones disponibles.
4. Ingresar la cantidad de créditos a usar.
5. Confirmar — el cambio se aplica de inmediato.

---

### Opción A — Aumentar Límite de Ventas *(PERMANENTE)*

| Característica | Detalle |
|----------------|---------|
| Efecto | +Bs. 5,000 de límite mensual por cada crédito usado |
| Duración | **Permanente** — se mantiene aunque el plan se renueve o cambie |
| Acumulación | Se suma al límite anterior (acumulativo) |
| Cálculo | `Límite total = Límite del plan + (créditos usados × 5,000)` |

**Ejemplo:** Un merchant con plan EmprendeYa (límite Bs. 40,000) usa 4 créditos en límite:
```
Límite base:        Bs. 40,000
Créditos (4 × 5k): +Bs. 20,000
──────────────────────────────
Límite total:       Bs. 60,000
```

Este aumento es **permanente** — al mes siguiente, cuando el plan se renueve, el límite seguirá siendo Bs. 60,000 sin necesidad de volver a comprar créditos.

> Ideal para negocios que tienen un volumen de ventas consistentemente por encima del límite base del plan.

---

### Opción B — Combo de Expansión *(30 DÍAS)*

| Característica | Detalle |
|----------------|---------|
| Efecto | +1 tienda adicional + 1 empleado adicional por crédito usado |
| Duración | **30 días** desde la fecha de activación |
| Vencimiento | Al expirar, los empleados extras se bloquean automáticamente |
| Renovación | Comprar y usar más créditos para extender otros 30 días |

**Ejemplo:** Un merchant con plan EmprendeYa (1 tienda, 1 empleado) usa 2 créditos de combo:
```
Tiendas base:  1
Combo (×2):   +2
────────────────
Total:         3 tiendas habilitadas por 30 días

Empleados base:  1
Combo (×2):     +2
──────────────────
Total:           3 empleados habilitados por 30 días
```

**¿Qué pasa al vencer el combo?**
- El sistema detecta los combos expirados automáticamente.
- Los empleados que superen el límite base del plan quedan con estado **bloqueado**.
- Los empleados bloqueados no pueden iniciar sesión hasta que se reactive el combo o se cambie a un plan con más capacidad.
- Las tiendas extra dejan de estar disponibles para nuevas ventas.

> Ideal para temporadas altas (fiestas, eventos, liquidaciones) o para probar la expansión antes de subir de plan.

---

## Sección 5 — Historial de créditos

En la pantalla de Suscripción se muestra el **historial completo de movimientos** de créditos.

### Tipos de movimientos

| Tipo | Ícono | Color | Qué indica |
|------|-------|-------|------------|
| **Compra** | Tarjeta | Azul | Créditos adquiridos por pago QR |
| **Uso - Límite extra** | Gráfico | Verde | Créditos aplicados para aumentar límite de ventas |
| **Uso - Combo extra** | Tienda+Personas | Morado | Créditos aplicados para combo de expansión |

### Datos de cada movimiento

- Tipo de movimiento
- Estado: **Acreditado** (disponible para usar) o utilizado
- Descripción (ej: "Aumento PERMANENTE de límite de ventas: +Bs. 10,000")
- Fecha y hora exacta
- Cantidad de créditos (+/-)
- Valor en Bs.

Los movimientos se ordenan del más reciente al más antiguo.

---

## Sección 6 — Créditos y renovación del plan

Al renovar el plan mensual o anual, los créditos se comportan así:

| Tipo de crédito | Al renovar el plan |
|-----------------|-------------------|
| **Créditos disponibles** (comprados, no usados) | Se preservan — pasan al nuevo ciclo |
| **Límite extra acumulado** (Opción A) | **Se preserva permanentemente** — el nuevo ciclo ya incluye el extra |
| **Combo activo** (Opción B, dentro de 30 días) | Se preserva si el combo aún no expiró |
| **Combo vencido** (más de 30 días) | No se preserva — solo se mantienen los combos dentro de su ventana de 30 días |

> Al cambiar de plan (upgrade/downgrade), los créditos de límite acumulados también se preservan. El nuevo plan simplemente cambia el límite base; el extra acumulado se suma al nuevo base.

---

## Preguntas frecuentes

**¿Puedo comprar créditos con cualquier banco?**

Sí. El pago se realiza por QR, compatible con cualquier banco boliviano que use la red BNB o Red Enlace. También se puede pagar con el banco activo del negocio.

**¿Los créditos tienen fecha de vencimiento?**

Los créditos de tipo "Límite de Ventas" no vencen — son permanentes. Los créditos de tipo "Combo de Expansión" tienen vigencia de 30 días desde su activación.

**¿Qué pasa si uso créditos de combo y no renuevo a tiempo?**

Los empleados que superen el límite base del plan quedan bloqueados automáticamente al vencer los 30 días. Para reactivarlos, basta con comprar y usar nuevos créditos de combo.

**¿Puedo mezclar créditos de límite y combo?**

Sí. Se pueden usar unos créditos para aumentar el límite de ventas y otros para el combo. Cada uso se gestiona de forma independiente.

**¿Cuántos créditos puedo comprar a la vez?**

No hay un límite máximo. Se puede comprar la cantidad necesaria en una sola transacción.

**¿Si cambio de plan pierdo los créditos acumulados?**

No. Los créditos disponibles (no usados) y el límite extra acumulado se preservan al cambiar de plan. Solo cambia el límite base.

**¿Cómo sé cuántos créditos tengo disponibles?**

En la pantalla de Suscripción se muestra el balance actualizado en tiempo real. También se puede ver el historial completo de compras y usos.

**¿Los créditos sirven para pagar la suscripción mensual?**

No. Los créditos solo sirven para ampliar el límite de ventas o agregar tiendas/empleados temporalmente. El pago de la suscripción se realiza por separado.
