---
name: specialize
description: Before assisting on a subject where basic intuition is not enough (a method, psychology, any discipline with a literature of its own), search for theory and evidence, come back with verified competence and crystallise it into a knowledge pill. Use for "specialise on X", "go find the best practices", or when about to set up a path or an analysis on general knowledge alone, in a field where established research exists.
---

# Specialize

*v1.0*

Goal: before assisting the user on a subject with a literature of its own, the assistant specialises instead of answering on intuition — it searches, comes back with verified competence, and crystallises it into a pill.

## Steps

1. **Define the gap** — list the 3-6 questions that basic knowledge would answer with received wisdom. Those are the ones to verify.
2. **Check existing assets** — read `00_context/knowledge_pills/index_knowledge-pills.md`: if a pill already covers the subject, use that one (updating it if needed) rather than creating a duplicate (Rule 4 of `CLAUDE.md`).
3. **Targeted search** — one search per question, not a generic one: aim for studies with an author and a year, meta-analyses, effect sizes. Prefer primary evidence or evidence syntheses over motivational content; flag it when the evidence contradicts common sense — that is the main value of the exercise.
4. **Distil into a pill** — write it in `00_context/knowledge_pills/`, one paragraph per pillar (what the evidence says + an "In practice:" line), a typical-mistakes section, linked sources. Dense, not long. Entry in the index in the same operation (Rule 1). Detailed format: [knowledge-pill](../../atomiche/knowledge-pill/SKILL.md).
5. **Come back with a position** — not a summary of the research: the answer to the concrete case in the light of the evidence, including the corrections to whatever was about to be done.

## Hard rules

- Different from [knowledge-pill](../../atomiche/knowledge-pill/SKILL.md): that one distils competence already surfaced in the sessions, this one goes and fetches it from outside.
- Without access to an external search this skill is not run from memory: state the limit and carry on, declaring that the answer is intuition, not verified.
- Evidence is cited, not invoked: a pill with no linked sources is not the output of this skill.
