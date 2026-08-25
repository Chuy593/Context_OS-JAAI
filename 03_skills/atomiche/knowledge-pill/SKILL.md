---
name: knowledge-pill
description: Distils a recurring competence — not domain knowledge — into a dense operational file saved in 00_context/knowledge_pills/, to call up instead of explaining it again. Use for "make me a pill on X", "create a cartridge", or when you notice you have explained the same thing across several sessions.
---

# Knowledge pill

*v2.0*

Goal: stop rebuilding the same reasoning every session. A pill is competence on loan: call it up, apply it, put it away.

## Steps

1. **Check it really is a pill** — a method reusable regardless of subject (a copywriting structure, a sales method, a way to run an interview), not research or data about a specific domain (that lives in `02_wiki/`). The test: "does this stay useful if I change project or client completely?" Yes → pill. No → wiki. If a nearby pill already exists, propose extending it instead of creating a second one.
2. **Gather the sources** — documents, research, transcripts, real notes. A pill written from memory is worth an opinion. If the sources are not there, say so and stop instead of padding it with generalities.
3. **Distil, don't summarise** — a summary tells you what the source says, a pill tells you what to do. File structure: title, 1-2 lines on what it is for and when to call it up, `## When it applies` (concrete situations, at least one example tied to the user's real work), `## How it's done` (dense method, no introductions or historical context), `## Typical mistakes` (only the ones that actually cost something), `**Sources:**` footer.
4. **Save and index it** — `00_context/knowledge_pills/<name>.md` in kebab-case. Entry in the folder's index in the same operation: a pill that is not indexed will never be called up.
5. **Clarity check** — before closing, explain in your own words (not by pasting the file) what the pill does, when it applies, how it is triggered, with an example tied to the real context. If the user has not understood, the file needs rewriting, not just re-explaining out loud.
6. **State how to use it** — close with the exact sentence to call it up in future (e.g. "read the pill on X and apply it to this text").

## Hard rules

- A pill replaces a repeated line of reasoning, not a reference document. Past 2-3 pages, it is probably two pills.
- Pills age: when one turns out to be inaccurate, fix it straight away instead of working around it in conversation.
- **Triggering is never automatic.** A pill stays silent until the user, or a skill that explicitly calls it, asks for it to be read and applied. Noticing a pattern that would deserve a pill during a conversation is conversational proactivity (Rule 9 of `CLAUDE.md`), not a mechanism of the pill itself.
