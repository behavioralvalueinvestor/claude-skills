---
name: handoff
description: Compact the current conversation into a handoff document, saved to the repo's handoffs/ directory, for another agent or a fresh session to pick up.
---

# Handoff

Write a handoff document that lets a fresh agent continue this work without re-reading the whole conversation. Capture state and intent, not a transcript.

## Where to save

Save the handoff inside the current project repo — never the OS temp directory, never inline in chat.

1. Resolve the repo root: run `git rev-parse --show-toplevel`. If it fails (not a git repo), fall back to the current working directory.
2. Ensure a `handoffs/` directory exists at that root; create it if missing.
3. Write to `handoffs/<slug>-handoff-<UTC-timestamp>.md`, where:
   - `<slug>` is a short kebab-case topic derived from the task (or from the arguments, if any were passed), e.g. `notebook-proxy-review`.
   - `<UTC-timestamp>` is `YYYYMMDDTHHMMSSZ`, e.g. `20260527T144059Z`.
   The timestamp keeps each handoff distinct — never overwrite an existing handoff.
4. After writing, print the absolute path of the file you created.

## What to write

If arguments were passed to this skill, treat them as the next session's focus and bias every section toward it.

Use these sections. Keep each within its cap; a handoff is a pointer document, not a record of everything. Omit any section that is genuinely empty rather than padding it.

- **Header** — title, date (UTC), and one line on what the next session is for. (≤5 lines)
- **Objective** — the goal and its success criterion. (≤3 sentences)
- **Current state** — what is done, what works, what is verified vs. assumed. (≤10 bullets)
- **Next steps** — concrete, ordered actions for the next agent. (≤8 bullets)
- **Key decisions & rationale** — locked choices and why, so the next agent doesn't relitigate them. (≤8 bullets)
- **Gotchas / landmines** — traps already hit, surprises, things that look done but aren't. (≤8 bullets)
- **Relevant files & references** — paths and URLs to code, PRDs, plans, diffs, issues. Reference them; do not inline their contents. (≤12 entries)
- **Open questions** — unresolved decisions that need the user or further work. (≤6 bullets)
- **Suggested skills** — skills the next agent should invoke, each with a one-line why. (≤6 entries)

## Rules

- Do not duplicate content already captured in other artifacts (PRDs, plans, ADRs, issues, commits, diffs). Reference them by path or URL instead.
- Do not paste large file contents or full command output into the handoff. Point to the source.
- Redact secrets and PII — anything matching API_KEY / SECRET / TOKEN / PASSWORD / PRIVATE_KEY or personal data. Local file paths are fine.
