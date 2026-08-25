# skills — index

> The system's skills, split by nature into **atomiche/** (atomic) and **flusso/** (flow). One folder per skill, `<name>/SKILL.md` with a YAML block at the top (name and description). This is the readable, editable source. Claude Code does not scan `03_skills/`: it discovers skills from `.claude/skills/`, which in this package already ships a ready copy of the same folders and stays **flat** (that is the execution location, not the reading one) — so on Claude Code they work with no user action. On claude.ai/app, which doesn't read `.claude/`, install them by copying each `SKILL.md`'s content into a new skill from settings.
> The cascade towards everything under `03_skills/` starts here.

## How they split

- **Atomic** — one input, one output, no decision inside. It knows nothing about the context it runs in, so any flow can call it. It carries the rules of its own craft (spending caps, parameters, checks), so whoever uses it does not have to remember them.
- **Flow** — a sequence that orders the work and hands it to a verdict from the user. Its value is the order and the gates, not the work: it points at atomic skills instead of re-explaining every step.

The user's final verdict is **not** what tells the two apart: almost everything ends with a decision of theirs. The line is whether the unit is callable from other flows.

**Entry criterion for a new atomic skill:** the operation has already been done by hand at least twice, **or** it carries a rule that, forgotten, costs money or damage. The second case matters most: a rule that depends on remembering it does not hold — it has to be attached to the step that executes it, and for a repeatable operation that step is the skill.

**The description is what makes a skill fire**, not its name: it must contain the words you use in the moment of need, not the technical name of what it does. `"metrics analysis"` matches nothing; in the moment of need you say *"how much traffic is it doing"*, *"what's my margin"*.

A procedure that already has a shape but has not yet passed the entry criterion lives as a flat folder `<name>/` at the root of `03_skills/`, in neither of the two: that is incubation.

## Atomic

- **[knowledge-pill/SKILL.md](atomiche/knowledge-pill/SKILL.md)** — distils a recurring competence into an operational file to call up, saved in `00_context/knowledge_pills/`.
- **[session-log/SKILL.md](atomiche/session-log/SKILL.md)** — closes a block of work by writing a dated entry in the monthly dump.
- **[correo-jesus/SKILL.md](atomiche/correo-jesus/SKILL.md)** — redacta un correo en el estilo real de Jesús Almaguer (tono, cierres, estructura). Reusable en cualquier proyecto, no solo Optimus Steel.
- **[analisis-presentacion-pdf/SKILL.md](atomiche/analisis-presentacion-pdf/SKILL.md)** — analiza un deck/PDF de presentación por consistencia financiera, mensaje ejecutivo, narrativa y riesgos, sin describir slide por slide.
- **[analisis-transcripcion-reunion/SKILL.md](atomiche/analisis-transcripcion-reunion/SKILL.md)** — extrae acuerdos, acciones, responsables, riesgos e inconsistencias de una transcripción de reunión.

## Flow

- **[onboarding/SKILL.md](flusso/onboarding/SKILL.md)** — first run: leads 3+1 questions, fills in `memory.md`, opens the first project. It is triggered by the first-run rule in `CLAUDE.md` while the system is still empty: the only one that is not installed as a separate skill.
- **[librarian/SKILL.md](flusso/librarian/SKILL.md)** — sorts `01_raw/` between knowledge and projects: atomic notes in the wiki, folders and state in `10_projects/`, indexes updated, originals archived in `_processed/` and contradictions flagged instead of overwritten.
- **[project-kickoff/SKILL.md](flusso/project-kickoff/SKILL.md)** — opens a new project: folder, `CLAUDE.md`, `memory.md`, row in the active projects table and entry in the index.
- **[specialize/SKILL.md](flusso/specialize/SKILL.md)** — before assisting on a subject with a literature of its own, fetches external evidence and crystallises it into a pill, instead of answering on intuition. Calls [knowledge-pill](atomiche/knowledge-pill/SKILL.md).
- **[system-check/SKILL.md](flusso/system-check/SKILL.md)** — mechanical checks on the system (broken links, orphan files, stale paths, naming, date discrepancies) plus, on a periodic run, the judgement layer: duplicated content, rules drifting from reality, repeated patterns in the feedback log.
- **[cost-review-mensual/SKILL.md](flusso/cost-review-mensual/SKILL.md)** — análisis del cost review mensual de Optimus Steel (cost per ton, producción vs. presupuesto, variaciones, causa raíz, riesgo) y redacción del Executive Summary en el formato real usado en los cost meetings.
- **[analisis-salud-metabolica/SKILL.md](flusso/analisis-salud-metabolica/SKILL.md)** — análisis multidisciplinario (13 especialidades) de salud metabólica, hormonal y cardiovascular de Chuy: evaluación de suplementos/alimentación/ejercicio/sueño con nivel de evidencia, interpretación integral de laboratorios y generación del dashboard metabólico.

---
*Editing a skill means editing it here, in `03_skills/<nature>/<name>/SKILL.md`: it's the single source. To reach Claude Code it also needs re-copying onto its twin folder in `.claude/skills/<name>/`, which stays flat (not an automatic link); for claude.ai/app, reload it from settings.*
