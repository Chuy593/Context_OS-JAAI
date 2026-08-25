---
name: system-check
description: Mechanical checks on the second brain (broken links, orphan files, stale paths, non-conforming naming, macro/micro date discrepancies) plus, on a periodic run, the judgement layer (duplicated content, rules drifting from reality, repeated patterns in the feedback log). Use for "check the system", "run a cleanup", "check the vault".
---

# System check

*v2.0*

Goal: catch structural breakage with a repeatable check instead of discovering it by accident, plus the judgement the mechanical pass alone cannot see. It reports, it does not correct — fixes are decided with the user after the report.

## Steps

**Mechanical (1-7, deterministic — no interpretation, only comparison between files):**

1. **Get the real date with a command** — never infer it from the latest entries in the files.
2. **Map the structure** — list (do not read) all `CLAUDE.md`, `memory.md`, `archive.md`, `index_*.md` and `*_index.md` files in the vault, including every level of `10_projects/`. Structure only, not content: this is the list the checks below run against.
3. **Broken or ambiguous links** — for every wikilink `[[ ]]` or path link in the mapped files: verify it resolves to exactly one file. Flag both links to nothing and ambiguous ones (several files with the same name).
4. **Orphan files** — files inside an indexed folder (`02_wiki/*`, `03_skills/`, etc.) that appear in no index of their category: unreachable through the cascade even though they exist on disk (Rule 1 of `CLAUDE.md`).
5. **Stale paths** — references to paths that no longer exist on disk (folders renamed, moved, flattened). Compare the paths written in the files against the real tree.
6. **Non-conforming naming** — files that break the current conventions (kebab-case for wiki notes, the two-level `*_index.md` / `index_<category>.md` scheme for folders — the full list lives in `99_system/operating-manual.md`).
7. **Macro/micro date discrepancies** — for every project in the "Active Projects" table of the root `memory.md`: compare the "Last updated" date with the one in that project's own `memory.md`. Every mismatch is a candidate for missed propagation.

**Judgement (8-10, these require reading and interpretation — only on the periodic run, not every execution):**

8. **Duplicated content** — the same fact written in more than one `memory.md` instead of living in one place with a pointer elsewhere (Rule 4 of `CLAUDE.md`).
9. **Rules drifting from reality** — compare the written rules (`CLAUDE.md` at every level, `99_system/operating-manual.md`) with the practice observed in `00_context/dump/` (recent period) and in the `memory.md` files. Flag where a rule is no longer followed, or where practice has moved past the rule without the rule being updated.
10. **Repeated patterns** — read `00_context/dump/` (recent period) and `99_system/system-feedback.md`: corrections or feedback that keep coming back to the same point are candidates to become a new rule in `CLAUDE.md`, instead of staying scattered reminders.

**Final report** — a list by category (broken links, orphans, stale paths, naming, date discrepancies, duplicated content, rules drifting from reality, repeated patterns), each with the file and line involved. No changes applied in this run.

## Hard rules

- **It reports, it does not correct.** Fixes are decided with the user after the report, step by step or in one batch — never applied on the assistant's own initiative.
- **On demand → steps 1-7 only.** The judgement pass (8-10) belongs to a periodic run: it costs more and needs interpretation, not just comparison.
- **Prerequisite:** the whole vault root mounted, not a specific project. Steps 8-10 also need `00_context/dump/` and `99_system/system-feedback.md` reachable.
