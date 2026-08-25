---
name: analisis-transcripcion-reunion
description: Analiza la transcripción de una reunión más allá de resumirla — extrae acuerdos, acciones con responsable, riesgos, inconsistencias y decisiones importantes. Usar para "analiza esta transcripción", "qué se acordó en esta reunión", "revisa la junta de costos".
---

# Análisis de Transcripción de Reunión

*v1.0*

Atómico: una entrada (la transcripción), una salida (el análisis estructurado). No decide el contexto de negocio — lo trae el proyecto que lo llama.

## Qué NO hacer

No entregar solo un resumen narrativo de lo que se habló.

## Qué extraer, siempre explícito

- **Acuerdos** — qué se acordó, en las palabras más cercanas posibles a lo dicho.
- **Acciones** — cada tarea que quedó pendiente, con su responsable si se mencionó (si no se mencionó responsable, decirlo explícitamente en vez de omitirlo).
- **Riesgos** — mencionados en la reunión o identificables por lo que se discutió (ej. una variación que "puede repetirse el próximo mes").
- **Inconsistencias** — contradicciones dentro de la misma reunión, o contra datos/documentos ya conocidos (presentación, cost review del mes).
- **Decisiones importantes** — quién decidió qué, y si quedó condicionado a algo.
- **Temas pendientes** — lo que se mencionó pero no se cerró ni se convirtió en acción.
- **Errores técnicos** — si durante la conversación alguien afirma algo técnicamente incorrecto (SAP, contabilidad de costos, controlling), señalarlo explícitamente como hallazgo aparte.

## Si hay presentación asociada

Cruzar contra el deck (ver [[../analisis-presentacion-pdf/SKILL.md]]) y señalar inconsistencias entre lo presentado y lo discutido.

---
*Fuente: Project "Optimus Steel" de claude.ai (sección "Transcripciones de reuniones"), migrado a Context OS el 2026-08-25.*
