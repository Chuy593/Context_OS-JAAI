---
name: project-kickoff
description: Opens a new project in the second brain — folder, CLAUDE.md, memory.md, row in the "Active Projects" table and entry in the index, so it is reachable from the Router straight away. Use for "open a new project", "project kick-off", or whenever a new line of work is born in 10_projects/.
---

# Project kickoff

*v2.0*

Goal: stop projects being born without a `CLAUDE.md`/`memory.md`, or without a row in the root table — the two most frequent holes.

## Steps

1. **Check it does not already exist** — grep/glob on the name, synonyms, domain. If something close already covers the same need, propose that before creating from scratch.
2. **Weigh it** — one question: will this project accumulate decisions and state over time that you will need to re-read a week from now?
   - No (a routine producing repeated output, no decisions to re-read) → skip steps 3-4, an operational file with 2 lines at the top is enough. If it is that light, consider whether it belongs in `03_skills/` as a procedure rather than in `10_projects/` as a project.
   - Yes (clients, live channels, decisions that change) → full scheme.
3. **Folder + CLAUDE.md** — copy `99_system/templates/claude-template.md` to `10_projects/<name>/CLAUDE.md`: role in one line, scope (what belongs, what does not and where the rest goes), internal structure only if it is not obvious, rules inherited from root made explicit.
4. **memory.md** — copy `99_system/templates/memory-template.md` to `10_projects/<name>/memory.md`, fill in the header, delete the sections that stay empty.
5. **Row in the "Active Projects" table** of the root `memory.md` — correct path, status "Active", next step in one sentence. Same session, it is a macro event. This applies to the light projects of step 2 too.
6. **Entry in `10_projects/projects_index.md`** — same operation. Without it the project exists on disk but is unreachable through the cascade (Rule 1). Two distinct writes: the table carries the state, the index carries reachability.
7. **`archive.md` — only when needed.** Do not create it at kick-off: it is born the first time a state in `memory.md` is replaced, not added to. It does not apply to light projects.

## Hard rules

- Kick-off always in the root chat, never inside a project chat.
- If the project is born by moving or merging content that already exists elsewhere, scaffolding is not enough: also apply "always links, never free-text paths" and check (grep) every reference to the old path.
- If it is not clear in one sentence what the new project does, ask before proceeding.
