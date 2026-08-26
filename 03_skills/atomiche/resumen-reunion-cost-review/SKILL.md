---
name: resumen-reunion-cost-review
description: Convierte la transcripción de una reunión semanal de Cost Review (cualquier área — Scrap Yard, Melt Shop, Rolling Mill, Support) en un resumen estructurado con 📋 Summary por elemento de costo y ✅ Follow ups con responsable. Salida en inglés, voz de equipo, nombres reales de proveedor. Usar para "resume esta reunión", "haz el weekly summary del cost review", "resume la transcripción de [área]", "SY/MS/RM cost review summary".
---

# Resumen de Reunión — Cost Review (cualquier área)

*v1.0*

Atómico: una entrada (transcripción de una reunión de cost review, normalmente `.docx` exportado de Teams), una salida (resumen semanal en el formato fijo 📋 / ✅). Genérico para cualquier área productiva; **no** decide de qué área es ni el contexto de negocio — eso lo trae quien lo llama o se infiere del propio contenido de la reunión.

**Dispara con:** el usuario sube una transcripción de una junta de cost review y pide resumirla / sacar los follow-ups, para cualquier área.

## Idioma

- **Output siempre en inglés**, aunque la transcripción venga en español o spanglish.
- Las preguntas de aclaración al usuario van en el idioma en que él escribe.

## Paso 1 — Leer la transcripción

Las transcripciones de Teams vienen con mucho ruido (spanglish, frases sueltas, timestamps por hablante, nombres de proveedor mal transcritos). Pipeline:

- Extraer texto con `extract-text <archivo>` o `pandoc -t markdown`; quitar artefactos de imagen (`grep -v '^!\['`).
- Si es larga, leer por chunks (~300–400 líneas) — no intentar todo de una.
- Filtrar el ruido conversacional; quedarse con el contenido de costo: montos, presupuesto vs. actual, proveedores, causas, pendientes y quién queda a cargo de qué.

## Paso 2 — Estructura de salida (fija)

```
[Área abreviada] Cost Review – [fecha]

📋 Summary
- Month-to-date status / overview: [una línea con el estado global — actual vs. budget si está]
- [Elemento de costo]: [budget vs. actual si está] — [1 línea]
  - [Proveedor] – $[monto]: [qué es / causa]
  - ...
- ...

✅ Follow Ups / Actions
- [Responsable] – [acción clara y específica]
- ...
```

- **Título:** abreviatura del área + "Cost Review" + fecha (ej. `SY Cost Review – August 20, 2026`, `MS Cost Review – …`).
- **📋 Summary:** un bullet por **cada elemento de costo que aparezca en la reunión** — no una lista fija. Según el área serán unos u otros (Scrap Cut, Rentals, Leasing, Logistics, Diesel, Payroll, Depreciation, Storeroom / Electricity, Gases, Refractories, Electrodes, Fluxes / Rolls & Guides, Tie Wire / cost centers de Support, etc.). No forzar elementos que no se discutieron.
- **Sub-bullets por proveedor/tema** dentro de los elementos que se desglosan factura por factura (típicamente Maintenance, Rentals, Leasing): formato `Proveedor – $monto: descripción`.
- **✅ Follow Ups:** responsable + acción concreta. Si en la reunión no se nombró responsable, decirlo explícito (`Owner TBD`), no inventarlo.

## Paso 3 — Reglas de contenido

- **Voz de equipo, nunca primera persona:** "The team reviewed / discussed / agreed…".
- **Nombres reales de proveedor, nunca genéricos** ("unfamiliar supplier", "a vendor" están prohibidos). Si un nombre viene mal transcrito y no es verificable, usarlo como mejor se entienda **y listarlo aparte** (ver Paso 5) para que el usuario lo confirme — no meter la duda dentro del entregable.
- **Cifras:** budget vs. actual cuando estén disponibles; formato `$X`, `$XK`, `$X.XM`. Marcar explícito lo **no presupuestado** cuando la reunión lo señale.
- **Conciso y factual:** sin relleno, sin adjetivos innecesarios, sin interpretación más allá de lo dicho.
- Una versión que el usuario marque como **final/corregida supera** este borrador y pasa a ser la fuente de verdad para consolidados posteriores.

## Paso 4 — Reglas de neutralidad (críticas, no negociables)

El resumen se comparte con el equipo y con leadership. **Nunca** incluir:

- Opiniones personales o juicios.
- Tensiones internas, fricciones, quejas entre áreas o personas.
- Cambios de personal, reorganizaciones, rotación.
- Menciones de que alguien "no respondió", "no entregó", "va atrasado" en términos que expongan a una persona.
- Cualquier cosa que exponga negativamente a un individuo.

Reformular el **estado del elemento de costo**, no la conducta de la persona. Ejemplo:
- ❌ "Martin no ha registrado ninguna factura de logística."
- ✅ "Logistics: no invoices posted as of the review date; team to follow up so pending charges are reflected."

El overtime por brechas de headcount / entrenamiento de nuevos ingresos **sí** es un driver operativo válido (aparece en los correos ejecutivos reales) — se reporta neutral y como causa de costo, no como señalamiento.

## Paso 5 — Nota de verificación (fuera del entregable)

Después del resumen, en mensaje aparte al usuario (no dentro del summary), listar los **nombres de proveedor / personas mal transcritos o dudosos** para que los confirme antes de tratarlos como fuente de verdad. Ej.: "State Fire y el proveedor de diésel venían confusos en el audio — confírmame la grafía y los fijo."

## Emojis

- `📋` y `✅` **solo** en los headers de este resumen semanal.
- **Nunca** en correos ni en el executive summary mensual.

## Qué NO hacer

- No resumir en orden cronológico ("primero hablaron de X, luego de Y") — organizar por elemento de costo.
- No inventar responsables, montos ni causas: si la transcripción no lo da, decir que falta.
- No mezclar áreas: el resumen es de la única área de la reunión (cada área tiene su propio hilo/proyecto).

## Relación con otras skills

- Para un análisis más profundo de la junta (acuerdos, riesgos, inconsistencias, errores técnicos) → [[../analisis-transcripcion-reunion/SKILL.md]]. Esta skill produce el **entregable de resumen**; la otra produce el **análisis**. Son complementarias.
- Para el consolidado mensual + executive summary a partir de los resúmenes semanales → [[../../flusso/cost-review-mensual/SKILL.md]] (esta skill alimenta a esa).

---
*Fuente: patrón de resúmenes semanales de Scrap Yard Cost Review (agosto 2026) + reglas de formato y neutralidad definidas por Jesús Almaguer. Generalizado a cualquier área.*
