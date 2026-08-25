---
name: cost-review-mensual
description: Analiza el cost review mensual de Optimus Steel (cost per ton, producción vs presupuesto, variaciones, causa raíz, riesgo) y redacta el Executive Summary para COO/CFO/CEO en el estilo real de Jesús. Usar para "cost review", "análisis mensual de costos", "executive summary de costos", "resumen ejecutivo del cost meeting", "redacta el summary de [mes]".
---

# Cost Review Mensual — Optimus Steel

*v1.0*

Flujo: primero se hace el análisis (causa raíz, no solo números), después se redacta el executive summary en el formato real usado en los cost meetings. Aplica a Scrap Yard, Melt Shop, Rolling Mill y Support Areas.

**Dispara con:** el usuario pide analizar o redactar el cost review/executive summary de un mes, o comparte datos de costo/producción de Optimus Steel para revisar.

**Contexto que este skill asume conocido:** [[../../02_wiki/optimus-steel/areas-productivas-optimus-steel]], [[../../02_wiki/optimus-steel/kpis-costos-manufactura]].

## Paso 1 — Análisis (nunca solo repetir números)

Prioridad fija, siempre en este orden:

1. Cost per Ton (real vs. budget, $/ton y %).
2. Producción vs. Presupuesto (tons, y si aplica yield).
3. Principales variaciones (variable vs. fijo, por área).
4. Causa raíz de cada variación relevante.
5. Riesgo para los siguientes meses (qué de esto se repite, qué revierte, qué es timing).

Para cada variación material, identificar explícitamente a cuál de estas categorías pertenece (ver `kpis-costos-manufactura.md` → "Categorías de causa raíz recurrentes"): operativa, financiera/timing-accrual, absorción/volumen, eficiencia, precio, evento extraordinario, o misclasificación contable. Nunca dejar una variación grande sin causa raíz explicada — si el dato no la da, decirlo explícitamente en vez de inventarla.

Siempre conectar el hallazgo contable con el impacto operativo (y con EBITDA/flujo cuando aplique) — el análisis nunca se queda en "subió/bajó $X".

## Paso 2 — Executive Summary

Audiencia: COO/CFO/CEO. Breve, claro, orientado al negocio. Nunca describir una tabla — debe responder: ¿qué pasó?, ¿por qué pasó?, ¿cuál fue el driver principal?, ¿qué debe preocuparnos?

### Estructura real (tomada de los correos de Jan/Feb/Mar/May 2026 en `01_raw/_processed/`)

```
Subject: Executive Summary – [Mes] [Año] Cost Review

Good afternoon,

Please find below the Executive Summary – [Mes] [Año] Cost Review, covering Scrap
Yard, Melt Shop, Rolling Mill, and Support Areas.

[Área 1: Scrap Yard]
Cost Performance
- Cost per ton: $X vs. $Y budget → +/-$Z (+/-%)
- Total Cost: $X vs. $Y budget → +/-$Z (+/-%)
- Handled/Produced Tons: X vs. Y budget → +/-Z tons (+/-%)

Production & Operational Performance
- [1-2 líneas: qué explicó el volumen]

Key Variances
Variable Cost Drivers
- [Concepto]: +/-$X (+/-%) driven by [causa raíz concreta]
Fixed Cost Drivers
- [Concepto]: +/-$X (+/-%) driven by [causa raíz concreta]

Comments
- [Hallazgos factuales adicionales, aclaraciones, correcciones en curso]

[Área 2: Melt Shop] (mismo formato, agrega Yield y Yield Impact)
[Área 3: Rolling Mill] (mismo formato, agrega Yield y Yield Impact)
[Support Areas] (Total Support Deviation + variaciones por cost center)

Overall Plant Summary
- [Área]: [una línea con el driver principal, tono ejecutivo]
- ... (una línea por área)

Regards,
Jesus [Almaguer / Cost & Finance, según el correo]
```

### Reglas de redacción del Executive Summary y del Overall Plant Summary

- El "Overall Plant Summary" al final es obligatorio cuando se cubre más de un área — es el cierre ejecutivo, una línea por área, con el driver principal, no un resumen de todos los números.
- Estilo de comentario de variación (para usar en Key Variances y en Overall Plant Summary): arranca declarando el resultado en $/ton o $ vs. budget, favorable o desfavorable, incluso si la producción cerró abajo o arriba del plan; después el driver principal; después el impacto de volumen si aplica; después las áreas responsables. Ejemplo real de la estructura: "Conversion cost closed $X.XX/ton favorable (or unfavorable) to budget despite production finishing below/above plan."
- Evitar frases repetitivas. No usar siempre "The variance was mainly driven…" — alternar la construcción de la frase manteniendo el lenguaje ejecutivo (ver los 4 correos de referencia: usan "driven by", "due to", "attributable to", "primarily due to" de forma variada).
- Formato de cifras: `$X.XX/ton`, cifras absolutas en `$XK` o `$X.XM`, variaciones con signo y % entre paréntesis, ej. `+$0.57 (+4%)` o `($1.27)/ton` para favorable.
- Comments (dentro de cada área) llevan hallazgos factuales que no caben en el bullet de variance: correcciones en curso, reclasificaciones contables, timing que se espera revierta, issues bajo investigación con el responsable (ej. "Natural gas metering discrepancy under review with Randy").

## Cuándo NO aplica este skill

- Si solo se pide explicar un concepto (Conversion Cost, Yield, etc.) sin datos de un mes específico → usar directamente `02_wiki/optimus-steel/kpis-costos-manufactura.md`, no este flujo.
- Si se pide redactar el correo de envío en sí (saludo, destinatarios, cierre) más allá del contenido del summary → complementar con [[../../atomiche/correo-jesus/SKILL.md]].

---
*Fuente: Project "Optimus Steel" de claude.ai (secciones "Análisis de Cost Review", "Executive Summary", "Estilo para Cost Reviews") + 4 correos reales de Executive Summary (Jan, Feb, Mar, May 2026), migrado a Context OS el 2026-08-25.*
