# Hábitos y Salud — Rules

> Optimización de la salud física, metabólica y mental de Jesús (Chuy) mediante recomendaciones basadas en evidencia y medicina preventiva, con visión multidisciplinaria (13 especialidades) y seguimiento longitudinal de biomarcadores.

Este archivo contiene solo reglas. El estado vive en `memory.md` de esta carpeta.

## Scope

Entra aquí: análisis de biomarcadores y estudios de laboratorio, seguimiento de peso/composición corporal/signos vitales, evaluación de suplementos, alimentación, ejercicio, sueño y manejo de estrés, generación del "dashboard metabólico", cualquier decisión de salud personal de Chuy.

No entra aquí (y va a otro lado):

- Metodología de análisis multidisciplinario, niveles de evidencia y formato de respuesta (reutilizable para cualquier consulta de salud) → skill `03_skills/flusso/analisis-salud-metabolica/SKILL.md`.
- Definiciones de biomarcadores y conocimiento de dominio, si se documentan más adelante → `02_wiki/habitos-salud/`.
- Identidad general y forma de trabajar de Jesús → `00_context/perfil-jesus.md`.

Test: "¿esto sigue siendo útil si cambia el dato pero no el método?" Es dato de hoy (peso, último laboratorio, hábito actual) → memory.md. Es método/regla reutilizable → skill o wiki.

## Estructura

- `memory.md` — estado actual: últimos biomarcadores registrados, objetivos vigentes, temas abiertos.
- `biometrics-log.csv` — histórico completo de mediciones de composición corporal y signos vitales, una fila por medición.
- `archive.md` — histórico de dashboards/evaluaciones cerradas (se crea la primera vez que se reemplaza un estado relevante en `memory.md`).

## Reglas heredadas de la raíz

- Propagación macro: esta conversación puede escribir directo en el `memory.md` raíz cuando cambia el status del proyecto o su next step — es un evento macro, se hace en la misma sesión.
- Memoria → Archivo: cuando se cierra una evaluación/dashboard y se reemplaza el estado en `memory.md`, la versión anterior se mueve primero a `archive.md` de esta carpeta antes de sobrescribirla.
- Single source of truth: la metodología (especialidades a integrar, niveles de evidencia, formato de respuesta) NO se repite aquí — está en `03_skills/flusso/analisis-salud-metabolica/SKILL.md`. Este archivo solo apunta a ella.

## Reglas específicas del proyecto

- Toda recomendación (suplemento, alimentación, ejercicio) se analiza considerando: beneficios, riesgos, contraindicaciones, nivel de evidencia, impacto metabólico/hormonal/cardiovascular/digestivo/renal, interacciones y costo-beneficio. Ver detalle completo en el skill.
- Prioridad de intervención, siempre en este orden: hábitos → alimentación → ejercicio → manejo de estrés → sueño → suplementos → fármacos (solo al final, cuando sea pertinente).
- Cuando exista conflicto entre recomendaciones de especialidades distintas, explicar el motivo y proponer la alternativa con mejor relación riesgo-beneficio — nunca ignorar el conflicto ni elegir una sola perspectiva en silencio.
- Cada vez que se registre un dato nuevo (peso, laboratorio, signos vitales), agregarlo a `biometrics-log.csv` y actualizar el resumen en `memory.md`; resaltar cambios importantes entre mediciones.
- No asumir que un síntoma (ansiedad, estrés, fatiga) es solo psicológico sin antes revisar la vía endocrina, de sueño y nutricional.

## Referencias

- Metodología multidisciplinaria, niveles de evidencia y formato de respuesta → [analisis-salud-metabolica](../../03_skills/flusso/analisis-salud-metabolica/SKILL.md)
- Histórico de biomarcadores → [biometrics-log.csv](biometrics-log.csv)

---
*Migrado desde el Project "Salud, Bienestar y Hábitos" de claude.ai el 2026-08-25: las instrucciones del proyecto se dividieron entre este archivo (estado/reglas del proyecto) y el skill de `03_skills/` (metodología reutilizable), en vez de vivir todas en un solo bloque de texto.*
