# Optimus Steel — Rules

> Contralor de Costos en Optimus Steel (siderúrgica/metalúrgica). Cubre cost review mensual, FP&A, controlling industrial en SAP S/4HANA (CO/FI/MM/PP) y el reporting ejecutivo derivado.

Este archivo contiene solo reglas. El estado vive en `memory.md` de esta carpeta.

## Scope

Entra aquí: cost reviews mensuales de Optimus Steel, análisis de variaciones de costo de manufactura, executive summaries para COO/CFO/CEO, correos relacionados a cost meetings, análisis de presentaciones/transcripciones de reuniones de la planta, decisiones de controlling (SAP CO/FI/MM/PP) específicas de esta operación.

No entra aquí (y va a otro lado):
- Procedimientos reutilizables (cómo se hace un cost review, cómo se redacta un correo estilo Jesús, cómo se analiza un PDF de presentación) → viven como skills en `03_skills/` y este proyecto solo los referencia.
- Definiciones de KPIs y de las áreas productivas (Scrap Yard, Melt Shop, Rolling Mill, Support Areas, Storeroom, Logistics, General Services, Engineering) → `02_wiki/optimus-steel/`.
- Identidad y forma general de trabajar de Jesús → `00_context/perfil-jesus.md`.

Test: "¿esto sigue siendo útil si cambio de cliente/empleador?" No (es específico de Optimus Steel) → aquí. Sí (es una técnica o definición reutilizable) → wiki o skill.

## Estructura

- `memory.md` — mes en curso: estado del último cost review, temas abiertos, riesgos para los próximos meses.
- `archive.md` — histórico de cost reviews cerrados (se crea la primera vez que se reemplaza un estado en `memory.md`).

## Reglas heredadas de la raíz

- Propagación macro: esta conversación puede escribir directo en el `memory.md` raíz cuando cambia el status del proyecto o su next step — es un evento macro, se hace en la misma sesión.
- Memoria → Archivo: cuando un cost review mensual queda cerrado y se reemplaza el estado en `memory.md`, el mes anterior se mueve primero a `archive.md` de esta carpeta antes de sobrescribirlo.
- Single source of truth: la metodología de análisis, el estilo de comentarios y el formato del executive summary NO se repiten aquí — están en `03_skills/flusso/cost-review-mensual/SKILL.md`. Este archivo solo apunta a ellos.

## Reglas específicas del proyecto

- Prioridad de análisis en cualquier cost review: (1) Cost per Ton, (2) Producción vs. Presupuesto, (3) principales variaciones, (4) causa raíz, (5) riesgo para los siguientes meses. Ver detalle completo en el skill de cost review.
- Áreas cubiertas cada mes: Scrap Yard, Melt Shop, Rolling Mill, Support Areas (y dentro de Support: Automation, Billet Yard, Storeroom, Engineering, General Services, Environmental, Quality Control, Maintenance Central, Safety).
- El nivel técnico de las respuestas debe corresponder al de un consultor senior SAP S/4HANA (CO/FI/MM/PP) — evitar explicaciones genéricas de controlling o de la industria.
- Todo análisis de resultados conecta el hallazgo contable con el impacto operativo y, cuando aplique, con EBITDA/flujo — nunca se queda solo en la variación numérica.

## Referencias

- Metodología de cost review + executive summary + estilo de comentarios → [cost-review-mensual](../../03_skills/flusso/cost-review-mensual/SKILL.md)
- Estilo de correo → [correo-jesus](../../03_skills/atomiche/correo-jesus/SKILL.md)
- Análisis de presentaciones (PDF) → [analisis-presentacion-pdf](../../03_skills/atomiche/analisis-presentacion-pdf/SKILL.md)
- Análisis de transcripciones de reunión → [analisis-transcripcion-reunion](../../03_skills/atomiche/analisis-transcripcion-reunion/SKILL.md)
- Áreas productivas → [areas-productivas-optimus-steel](../../02_wiki/optimus-steel/areas-productivas-optimus-steel.md)
- KPIs de costos de manufactura → [kpis-costos-manufactura](../../02_wiki/optimus-steel/kpis-costos-manufactura.md)
- Ejemplos reales de executive summary (fuente de los patrones de estilo, texto extraído — el PDF original queda en el Project de claude.ai) → `01_raw/_processed/cost-meeting-{jan,feb,mar,may}-2026-email-example.md`

---
*Migrado desde el Project "Optimus Steel" de claude.ai el 2026-08-25: las instrucciones del proyecto se dividieron entre este archivo (estado/reglas del proyecto), los skills de `03_skills/` (procedimientos reutilizables) y `02_wiki/optimus-steel/` (conocimiento de dominio), en vez de vivir todas en un solo bloque de texto.*
