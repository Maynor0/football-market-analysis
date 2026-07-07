# 📕 TUTORIAL COMPLETO: TARJETAV1 (VERSIÓN 2.0 PRO) - SISTEMA DE ANÁLISIS DE DISCIPLINA

**Versión:** 2.0 (Mejorada para Precisión Estadística)
**Mercado:** Tarjetas (Over/Under, Hándicap, Puntos por Tarjeta)
**Uso:** Complemento crítico para Cornv8 + Sistema independiente de beneficios

---

## 📋 ÍNDICE

1. [Introducción: La Disciplina es Matemáticas](#introducción)
2. [Estructura Avanzada de Datos (Nivel 2)](#estructura)
3. [El "Factor Árbitro" Ponderado (Foul-to-Card Ratio)](#arbitro)
4. [Métrica Clave: PADP (Possession Adjusted Discipline Profile)](#padp)
5. [Workflow Profesional: El Triángulo de Odio](#workflow)
6. [Gestión de Riesgo y Casas de Apuestas](#riesgo)
7. [Ejemplo Práctico Real](#ejemplo)

---

## 📍 1. INTRODUCCIÓN: LA DISCIPLINA ES MATEMÁTICAS {#introducción}

La versión 1.0 era buena para principiantes (mirar promedios simples).
La **Versión 2.0** elimina el ruido.

**El Problema de los Promedios Simples:**
*   Equipo A promedia 3 tarjetas por partido.
*   Equipo B promedia 3 tarjetas por partido.
*   **Conclusión V1:** "Habrá 6 tarjetas".
*   **Realidad:** Si el Equipo A juega contra el Man City (tiene 20% posesión), hará 5 tarjetas. Si juega contra el colista (60% posesión), hará 1 tarjeta.
*   **Solución V2:** Ajustar por **Posesión** y **Rigor Arbitral**.

---

## 🏗️ 2. ESTRUCTURA AVANZADA DE DATOS (NIVEL 2) {#estructura}

En tu archivo `TarjetaV1.xlsx`, vamos a refinar las columnas para medir la *intención* y no solo el resultado.

### Nuevas Columnas Sugeridas:

#### A. Para Árbitros
1.  **Fouls Per Card (FPC):** ¿Cuántas faltas necesita ver para sacar amarilla?
    *   *Ejemplo:* Gil Manzano (FPC = 5.2) vs Mateu Lahoz (FPC = 3.8).
    *   *Significado:* Mateu saca tarjeta mucho más rápido. FPC bajo = Árbitro Over.
2.  **Home Bias %:** ¿Qué % de tarjetas saca al visitante? (Crucial para apuestas de equipo).

#### B. Para Equipos
1.  **Faltas Cometidas por Partido (FCP):** El "motor" de las tarjetas.
2.  **Faltas Recibidas (Provocadas):** La "gasolina".
3.  **Ratio Tarjetas/Falta:** ¿Son faltas "tácticas" (agarrón = amarilla segura) o faltas "torpes" (empujón = solo falta)?

---

## 👮 3. EL "FACTOR ÁRBITRO" PONDERADO (Foul-to-Card Ratio) {#arbitro}

Ya no clasificamos solo por "Verde/Rojo". Usamos el **Índice de Leniencia**.

**Fórmula de Impacto Arbitral:**
```
Impacto = (Promedio Árbitro) / (Promedio Liga)
```
*   Liga Santander Media: ~4.8 tarjetas.
*   Árbitro X Media: 6.2 tarjetas.
*   **Impacto:** 1.29 (Este árbitro aumenta las tarjetas un 29% sobre lo normal).

**Cómo usarlo:**
Si tus equipos proyectan 4 tarjetas combinadas, multiplica por 1.29.
`4 * 1.29 = 5.16` → **Apuesta Over 4.5**.

---

## 📊 4. MÉTRICA CLAVE: PADP (Possession Adjusted Discipline Profile) {#padp}

Esta es la mejora de precisión masiva.

**Lógica:**
Un equipo que defiende el 80% del tiempo tiene *más oportunidades* de hacer falta que uno que tiene el balón.

**Regla de Ajuste (Simplificada para tu Excel):**
*   **Si el equipo va a tener POCO balón (<40%):** Aumenta su proyección de tarjetas un **+20%**.
*   **Si el equipo va a DOMINAR (>60%):** Reduce su proyección un **-20%**.

*Ejemplo:*
Getafe (Carniceros) juega contra Real Madrid.
*   Getafe no olerá el balón (30% posesión).
*   Getafe Media: 3.5 tarjetas.
*   Ajuste PADP: 3.5 * 1.20 = **4.2 tarjetas esperadas**.

---

## ⚔️ 5. WORKFLOW PROFESIONAL: EL TRIÁNGULO DE ODIO {#workflow}

Para apostar a Tarjetas con confianza alta, busca el **"Triángulo de Odio"**:

1.  **Vértice 1 (Agresor):** Equipo que hace muchas faltas (Fouls > 14 pp).
2.  **Vértice 2 (Provocador):** Rival con dribladores rápidos (Vinicius, Saka, Nico Williams).
3.  **Vértice 3 (Juez):** Árbitro con **FPC bajo** (< 4.5 faltas por tarjeta).

**Si tienes los 3 vértices:**
🔥 **APUESTA MÁXIMA (Stake Alto)** al Over de Tarjetas o Expulsión.

---

## ⚠️ 6. GESTIÓN DE RIESGO Y CASAS DE APUESTAS {#riesgo}

### El Truco de los "Puntos por Tarjeta" (Booking Points)
Muchas casas (Bet365, William Hill) usan puntos:
*   Amarilla = 10 ptos
*   Roja = 25 ptos

**Estrategia V2:**
Si el árbitro es "tarjetero" pero NO saca rojas (miedo escénico), apuesta al **Hándicap Asiático de Tarjetas (Over 4.5)**, no a puntos.
Si el árbitro pierde el control (muchas rojas), apuesta a **Puntos (Over 55.5)**, porque una roja te paga la línea sola.

---

## 📝 7. EJEMPLO PRÁCTICO REAL {#ejemplo}

**Partido:** Sevilla vs Getafe
**Árbitro:** Hernández Maeso (FPC = 4.2 - Muy Estricto)

**Análisis V1 (Básico):**
*   Sevilla media 2.8 + Getafe media 3.4 = 6.2.
*   Apuesta: Over 5.5.

**Análisis V2 (Preciso):**
1.  **Posesión:** Sevilla tendrá 65%. Getafe defenderá (35%).
2.  **Ajuste Getafe (PADP):** 3.4 * 1.20 (por no tener balón) = **4.1 tarjetas**.
3.  **Ajuste Sevilla:** 2.8 * 0.80 (por tener balón) = **2.2 tarjetas**.
4.  **Suma Equipos:** 6.3 tarjetas.
5.  **Factor Árbitro:** Hernández Maeso es Top 3 estricto (+15% sobre media).
6.  **Proyección Final:** 6.3 * 1.15 = **7.25 tarjetas**.

**Conclusión V2:**
El Over 5.5 es un regalo. La línea real debería ser 6.5 o 7.0.
**Valor Inmenso.**

---

### Resumen de Actualización para tu Excel
1.  Añade la columna **"Fouls Per Card"** en la hoja de Árbitros. (Dato clave).
2.  Añade una celda de **"Posesión Estimada"** en el análisis del partido.
3.  Usa la fórmula PADP mentalmente: "El que defiende, pega más".

Esto convierte tu `TarjetaV1` de una simple lista de promedios a un **modelo predictivo de comportamiento**.
