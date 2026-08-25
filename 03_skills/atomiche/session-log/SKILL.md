---
name: session-log
description: Closes a block of work by writing a short, dated entry in the monthly dump (00_context/dump/YYYY-MM.md) and returns the same recap in chat. Use for "log this", "write the dump", "close the session", "sum up what we did".
---

# Session log

*v2.0*

Goal: stop losing feedback, decisions and finished work that only ever existed in the conversation, or in the assistant's automatic memory, which is invisible to the user.

## Steps

1. **Decide the scope ("from when")** — look back through the conversation and find where the active block starts: usually the last clean change of subject, or the last dump already written in this session, whichever is more recent. If it is ambiguous, propose the scope in one line ("Summing up from X, right?") and wait for confirmation before writing.
2. **Filter first, then categorise** — a line earns its place only if it matters later: a behaviour to repeat or avoid, a decision worth re-reading, a fact that changes a project's state. Process details internal to the session do not qualify, even when true. When in doubt, 1-2 lines, not 4. Categories: `[feedback]` (a correction or preference that changes future behaviour), `[recap]` (what was done, decided or produced), `[other]` (an open thread with no answer yet).
3. **Write into the current month's dump** — get the real date with a command before naming the file. `00_context/dump/YYYY-MM.md`, create the file if the month does not exist yet, using the header already in use. Format: `- **YYYY-MM-DD [category]:** content in 1-2 lines.`
4. **Return the recap in chat** — paste the same lines just written, without reformatting or expanding them. No preamble.

## Hard rules

- It does not work on an empty or already closed chat: it needs a live conversation to extract the block from.
- If building the recap means reading long messages or several files, state an estimate of the tokens used and a cheaper alternative if one exists.
- Manual trigger, never automatic. If it ever becomes automatic: validate it over 2-3 manual runs first (an over-sensitive trigger writes noise the user then has to filter), and coordinate it with Rule 14 of `CLAUDE.md` (self-improvement log) so the same line is not written twice.
