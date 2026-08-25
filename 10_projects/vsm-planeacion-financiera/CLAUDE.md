# VSM Planeación Financiera — Reglas

Mapeo Value Stream Map (VSM) de todos los procesos del área de Planeación Financiera de Optimus Steel (presupuesto, forecast/reforecast, cierre y reporte mensual de costos por área operativa, seguimiento de CAPEX, modelos de costo estándar, reportes a corporativo), con la meta de construir un inventario maestro, documentar cada proceso a detalle y proponer un estado futuro optimizado.

Este archivo contiene solo reglas. El estado vive en memory.md de esta carpeta.

## Scope

Entra aquí: inventario maestro de procesos de Planeación Financiera, entrevistas de mapeo (disparador, pasos, sistemas, responsable, frecuencia, tiempo de ciclo, output, desperdicios), sincronización del inventario maestro en Smartsheet, decisiones sobre estructura y campos del inventario, seguimiento a personas y archivos individuales del equipo.

No entra aquí (y va a otro lado):

- El inventario maestro de procesos (tabla) y el directorio de personas del equipo, contenido reusable consultado en cada corrida, → 02_wiki/vsm-planeacion-financiera/.
- El procedimiento de sincronización a demanda entre los Excel individuales y Smartsheet → 03_skills/flusso/actualizacion-inventario-vsm/SKILL.md.
- Transcripciones y resúmenes de sesiones ya distilados (fuente original) → 01_raw/_processed/ (referencia, no se duplican aquí).
- Metodología de cost review mensual, un proyecto distinto con su propio alcance → 10_projects/optimus-steel/.

Test: "¿esto sigue siendo útil si cambia el área o el alcance del VSM?" No, es específico de esta iniciativa → aquí. Sí, es un procedimiento o dato reusable → skill o wiki.

## Reglas heredadas de la raíz

- Macro propagación: esta conversación puede escribir directo en el memory.md raíz cuando cambia el status del proyecto o su next step, es un evento macro, se hace en la misma sesión.
- Memoria → Archivo: cuando el estado de una corrida de sincronización queda superado en memory.md, el contenido anterior se mueve primero a archive.md de esta carpeta antes de sobrescribirlo.
- Single source of truth: el inventario maestro, el directorio de personas y el procedimiento de sincronización NO se repiten aquí, están en 02_wiki/vsm-planeacion-financiera/ y en el skill de actualización. Este archivo solo apunta a ellos.

## Reglas específicas del proyecto

- El campo "Prioridad de Mejora" del inventario en Smartsheet se llena en bloque una vez que todos los archivos individuales del equipo estén completos, nunca de forma incremental.
- Un proceso que desaparece del Excel de una persona se elimina automática e incondicionalmente de Smartsheet, con criterio conservador ante ambigüedad de coincidencia.
- Con más de 15 procesos nuevos detectados en una sola corrida: mostrar la lista completa al usuario y esperar confirmación antes de cargar masivamente.
- Automatización 100% en la nube (cron/routine remoto) no es viable por falta de acceso a las carpetas locales del equipo, el modo vigente es "a demanda", disparado explícitamente por el usuario.
- El análisis neutral y factual se mantiene siempre respecto a personas: el mapeo se enfoca en el proceso, nunca en el desempeño o fricciones de colaboradores específicos.

## Referencias

- Procedimiento de actualización del inventario maestro → 03_skills/flusso/actualizacion-inventario-vsm/SKILL.md
- Inventario maestro, borrador inicial y directorio de personas del equipo → 02_wiki/vsm-planeacion-financiera/
- Reunión SAP CO 13-ago-2026, fuente del borrador inicial de 16 procesos → 01_raw/_processed/vsm-reunion-sap-co-2026-08-13.md
- Entrevista de mapeo detallado, Daniel Agudelo, 18-ago-2026 → 01_raw/_processed/vsm-entrevista-daniel-agudelo-2026-08-18.md
- Resúmenes semanales de status → 01_raw/_processed/vsm-resumen-semanal-2026-08-18.md, 01_raw/_processed/vsm-resumen-semanal-2026-08-21.md

Migrado desde el Project "VSM Planeación Financiera Optimus Steel" de claude.ai el 2026-08-25: las instrucciones y los seis documentos del proyecto se dividieron entre este archivo, memory.md, la wiki, el skill de actualización y 01_raw/_processed/, en vez de vivir todos como archivos sueltos.
