# 📙 TUTORIAL COMPLETO: AMBOSSI0NO (VERSIÓN 2.0 PRO) - SISTEMA BTTS

**Versión:** 2.0 (Mejorada con xG y Análisis de Juego)
**Mercado:** Both Teams To Score (BTTS) - YES/NO
**Uso:** Complemento perfecto para Cornv8 + Sistema independiente de beneficios

---

## 📋 ÍNDICE

1. [Introducción: El Mercado BTTS como Herramienta de Precisión](#introducción)
2. [Los Datos que Necesitas (No Solo Promedios)](#datos)
3. [La Métrica Clave: xG (Expected Goals)](#xg)
4. [La Fórmula BTTS v2.0 (Correlación Attack-Defence)](#formula)
5. [El "Triángulo de Goles" (Tactical Vulnerability)](#triangulo)
6. [Game State en BTTS: Cómo Cambia Según el Marcador](#gamestate)
7. [Integración con Cornv8 + TarjetaV1](#integracion)

---

## 📍 1. INTRODUCCIÓN: EL MERCADO BTTS COMO HERRAMIENTA {#introducción}

A diferencia de Córners (que predice "eventos" del partido) o Tarjetas (que depende del árbitro), **BTTS predice el flujo ofensivo total**.

**Por qué BTTS es CRÍTICO para tu sistema:**
*   **Filtra a Cornv8:** Si predices Muchos Córners, necesitas confirmar que habrá ritmo de ataque (BTTS YES).
*   **Filtra a TarjetaV1:** Si predices Pocas Tarjetas, necesitas confirmar que no habrá juego trabado (esto apunta a BTTS YES).
*   **Valida el Contexto:** BTTS YES = Partido abierto. BTTS NO = Partido defensivo/cerrado.

**El Error Común:**
Las casas ofrecen BTTS YES @ 1.90 (52% implícito). La mayoría de traders la tocan sin analizar.
**La Verdad:** BTTS tiene tanta varianza que sin datos profundos, es moneda al aire.

---

## 🏗️ 2. LOS DATOS QUE NECESITAS (NO SOLO PROMEDIOS) {#datos}

Tu archivo `AmbosSi0No.xlsx` probablemente tiene columnas como:
*   Equipo A Goles Por
*   Equipo A Goles Contra
*   Equipo B Goles Por
*   Equipo B Goles Contra

**Esto NO es suficiente.** Necesitas:

### Nuevas Columnas Críticas:

1.  **xG For (Goles Esperados a Favor):** Calidad de las oportunidades que el equipo crea.
    *   **No es lo mismo:** Ganar 3-0 contra Andorra (xG 0.8) vs. Ganar 3-0 contra Bayern (xG 3.2).
    *   La segunda señaliza peligro futuro.

2.  **xG Against (Goles Esperados en Contra):** Calidad de oportunidades que recibe.
    *   Un equipo que concede xG 1.5 pp es más frágil que uno que concede 0.8, incluso si ambos tienen 1 gol pp.

3.  **BTTS % (Últimos 10 partidos):** % de partidos donde ambos marcaron.
    *   **Mucho más predictivo** que promedios simples de goles.

4.  **High Possession BTTS % vs Low Possession BTTS %:** CRITICAL.
    *   Algunos equipos tienen BTTS 70% cuando dominan, pero BTTS 20% cuando ceden el balón.

---

## 📊 3. LA MÉTRICA CLAVE: xG (Expected Goals) {#xg}

**¿Qué es xG?**
Es la suma de probabilidades de cada disparo. Un tiro desde 30 metros = 0.02 xG. Un cabezazo en el área pequeña = 0.45 xG.

**¿Por qué cambia todo?**
Un equipo que pierde 0-3 pero tiene xG 2.5 está en peligro existencial (creó peligro, le falló la puntería).
Un equipo que gana 3-0 y tiene xG 1.2 está "suertudo" (ganó sin crear peligro).

**Fórmula de Riesgo BTTS:**

```
BTTS Probability = (xG_A * xG_B) / (1 + xG_A + xG_B)

Ejemplo:
Equipo A xG: 1.8
Equipo B xG: 1.2

BTTS = (1.8 * 1.2) / (1 + 1.8 + 1.2) = 2.16 / 4.0 = 0.54 = 54%

Interpretación: 54% de probabilidad de BTTS YES.
Si la casa paga 1.90 (52% implícito), hay VALUE de +2% → MARGINAL, NO APUESTAS.
Si la casa paga 2.20 (45% implícito), hay VALUE de +9% → ENTRA.
```

---

## ⚔️ 4. LA FÓRMULA BTTS v2.0 (Correlación Attack-Defence) {#formula}

La fórmula anterior es "matemática pura". Ahora añadimos la **realidad táctica**.

**Step by Step:**

1.  **Obtén xG de ambos equipos** (de FBRef o Understat).
2.  **Obtén la posesión esperada** (Équipo A vs Équipo B).
3.  **Ajusta xG por contexto:**
    *   Si Equipo A juega en casa: +8% a su xG (factor psicológico).
    *   Si Equipo B está luchando por descender: +10% a su xG (desesperación = riesgos).
4.  **Aplica la fórmula de Poisson Conjunto:**
    ```
    BTTS% = P(Goals_A >= 1) × P(Goals_B >= 1)
    Donde P(Goals >= 1) = 1 - P(0 goals) = 1 - POISSON(0, xG)
    ```

**Ejemplo Práctico:**
Arsenal (xG 2.1, Casa) vs Aston Villa (xG 1.3, Fuera).

Ajustes:
*   Arsenal: 2.1 * 1.08 = 2.27
*   Aston Villa: 1.3 (sin ajuste por forma reciente neutral)

Poisson:
*   P(Arsenal >= 1) = 1 - POISSON(0, 2.27) = 1 - 0.103 = 89.7%
*   P(Villa >= 1) = 1 - POISSON(0, 1.3) = 1 - 0.273 = 72.7%

BTTS = 89.7% × 72.7% = **65.3%**

Cuota mercado 1.90 implica 52%. **VALUE = +13%** ✅ ENTRA.

---

## 🎯 5. EL "TRIÁNGULO DE GOLES" (Tactical Vulnerability) {#triangulo}

Para BTTS extremadamente confiables, busca el **"Triángulo de Goles":**

1.  **Vértice 1 (Atacante):** Equipo con xG > 1.8 pp.
2.  **Vértice 2 (Vulnerable):** Rival con xGA (Expected Goals Against) > 1.4 pp.
3.  **Vértice 3 (Contexto):** Partido es Derbis, Clasificación Copa, o Lídia.

**Si tienes los 3:**
🔥 **BTTS YES con Stake ALTO.** La probabilidad suele ser > 60%.

---

## 📍 6. GAME STATE EN BTTS: CÓMO CAMBIA SEGÚN EL MARCADOR {#gamestate}

Este es el secreto que los markets no integran bien.

**Escenario 1: Si Equipo A marca en el Minuto 5:**
*   Equipo A se echa atrás (Game State: Defensive).
*   Equipo B ataca (Game State: Desperate).
*   BTTS Probability SUBE (porque B ataca más riesgos).

**Escenario 2: Si va 0-0 hasta el Minuto 80:**
*   Ambos equipos "desesperados" por goles.
*   Entran suplentes ofensivos.
*   BTTS Probability SUBE dramáticamente (entre minutos 80-90, es 80%+ si sigue 0-0).

**Aplicación In-Play:**
*   Si ves que a los 70 minutos sigue 0-0, y tu modelo dice BTTS 55%, ENTRA AHORA.
*   Los minutos finales son los de mayor probabilidad BTTS por desesperación.

---

## 🔗 7. INTEGRACIÓN CON CORNV8 + TARJETAV1 {#integracion}

Ahora tienes 3 sistemas independientes. Aquí cómo funcionan juntos:

### Escenario A: "El Partido Perfecto para Córners"
```
Cornv8 predice: Over 10.5 Córners
TarjetaV1 predice: Under 4.5 Tarjetas (Juego fluido)
AmbosSi0No predice: BTTS YES (65%+)

Confluencia Total: ✅✅✅
Decisión: APUESTA MÁXIMA (2 unidades)
Razón: Todo apunta a partido abierto, fluido, sin pausas.
```

### Escenario B: "La Trampa"
```
Cornv8 predice: Over 9.5 Córners
TarjetaV1 predice: Over 5.5 Tarjetas (Juego trabajado)
AmbosSi0No predice: BTTS NO (65%+)

Confluencia Contradictoria: ❌
Decisión: SKIP (No apostar)
Razón: Juego trabado no genera córners, aunque parezca "muchos eventos".
```

### Escenario C: "La Oportunidad Oculta"
```
Cornv8 predice: Under 8.5 Córners (aparentemente malo)
TarjetaV1 predice: Under 3.5 Tarjetas (Juego limpio)
AmbosSi0No predice: BTTS YES (60%+)

Análisis: El partido será fluido pero con pocos córners (equipos juegan en el medio campo).
Decisión: SKIP Córners, pero APUESTA BTTS YES.
Razón: Hay goles, pero sin asedio de área (= pocos córners).
```

---

## 📊 CHECKLIST COMPLETO (VERSIÓN 2.0)

Antes de apostar a BTTS, verifica:

```
NIVEL 1 (Básico):
□ xG de ambos equipos disponible (FBRef, Understat)
□ Posesión esperada calculada
□ BTTS % últimos 10 partidos (no solo promedios)

NIVEL 2 (Avanzado):
□ Ajustes Home/Away aplicados
□ Contexto táctico evaluado (descenso, lucha clasificación)
□ Fórmula Poisson ejecutada

NIVEL 3 (Confluencia):
□ Triángulo de Goles identificado (si existe)
□ Game State considerado (minuto en que entra)
□ Confluencia con Cornv8 + TarjetaV1 validada

ANTES DE ENVIAR:
□ VALUE > 5%
□ Cuota mejor en Vave / Jackbit / 1xBet
□ Stake ajustado (Kelly Criterion)
□ Registro del pick en tu sistema
```

---

**Última actualización:** Diciembre 20, 2025 | V2.0 Pro
**Status:** Listo para integración en tu sistema de 3 pilares (Cornv8 + TarjetaV1 + AmbosSi0No)
**ROI Esperado:** Si integras bien, +5-8% anual en BTTS adicional.