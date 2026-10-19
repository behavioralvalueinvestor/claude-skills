---
name: grill-me
description: Interview the user relentlessly about a plan, design, or topic, checkpointing every answer to a brainstorm file so nothing is lost. Use when the user wants to stress-test a plan, get grilled on a design, run a brainstorm or discovery session, extract what's in their head into a doc, or says "grill me" or "/grill-me".
---

# Grill Me

Relentlessly interview the user about every aspect of the topic until you reach shared understanding. Walk down each branch of the decision tree, resolving dependencies one by one. The real goal is to **extract what's in their head into a durable, organized markdown file** so nothing is lost as context fills up.

## The capture file is the whole point

Long interviews fill up context. If you hold answers only in your head, you will eventually misremember, conflate, or drop something. So you **checkpoint to disk after every single answer**. The file, not your context, is the source of truth. Never make the user ask you to save progress.

## Setup (do this BEFORE the first question)

1. **Pick the session — resume or new.** Before creating anything, list the existing captures in `brainstorms/` (`Get-ChildItem brainstorms` in PowerShell, `ls brainstorms` in Bash). If any could plausibly match the topic the user is raising, read each candidate's `Goal:` line and show them — filename + goal, one line each — then ask whether to resume one or start fresh. Don't match on a re-derived slug; the user's wording shifts between sessions, so an exact-name guess silently forks the topic into a second file. Let the user choose. (You only see captures in the current directory's `brainstorms/`, so a session is resumable only from the directory it started in.)
   - **Resuming:** read the chosen file in full for the prior context, then continue appending to it — never overwrite.
   - **New** (or the folder is empty / nothing matches): continue to step 2.
2. **Create the capture file** at `brainstorms/{YYYY-MM-DD}-{topic-slug}.md`, relative to the current working directory (create the `brainstorms/` folder if it doesn't exist). The slug is the topic lowercased and kebab-cased, ~3–5 words (e.g. `pricing-model-for-pulse`). Each project keeps its own `brainstorms/` folder next to the work it is about, so captures stay with that work. If a session later produces a polished deliverable (a plan, an artifact), that deliverable can move into the relevant `projects/` folder, but the raw capture always stays in `brainstorms/`.
   - Get today's date with `Get-Date -Format 'yyyy-MM-dd'` (PowerShell), or `date +%F` (Bash), if you don't already know it.
   - If a file with that name already exists, add `-2`, `-3`, and so on before `.md` until the name is unused. Starting a new session never overwrites an existing capture.
3. **Create the file immediately** using the header in the Capture file format section below.
4. **Tell the user where you're saving** (or which file you're resuming), in one line. Then ask the next question.

## Capture file format

Header (write once at creation):

```
# {Topic} — brainstorm
Date: {YYYY-MM-DD}
Goal: {one line — what this session is deciding or extracting}

## Open questions
(empty for now; flagged items bubble up here)

## Log
```

Each entry, appended under `## Log` after every answer:

```
### {short question topic}
- **Asked:** {the question}
- **Answer:** {key facts / decisions, in their words where the wording matters}
- **Flags:** {couldn't-answer / open / contradicts-earlier — or "none"}
```

## The checkpoint rule (non-negotiable)

After EVERY user answer, BEFORE you ask the next question:
- Append an entry under `## Log` in the format above: the question topic, the key facts and decisions (in their words where the wording matters), and any flags. Bubble anything unresolved up to the `## Open questions` section.
- Update or correct earlier entries if a later answer changes them.
- Only then ask the next question.

Never batch multiple answers into one write. Checkpoint one answer at a time. The point is durability: if the session dies mid-interview, the file already holds everything answered so far.

## How to grill

- **Open by mapping the territory.** Start with what you are deciding and what success looks like before drilling into any one branch — you need the shape of the problem before the details.
- **One question at a time.** Never dump a list — each answer steers the next question.
- **Follow the branch.** When an answer opens a dependency or sub-decision, go down that branch and resolve it before backing out to the next sibling.
- **Push on vagueness.** If an answer is hand-wavy, hedged, or contradicts an earlier one, name it and ask again. You are grilling, not transcribing.
- **Surface assumptions and unknowns.** Ask what they are assuming, what they do not know yet, and what would change their mind.

## When to stop

- Stop when the decision tree is walked: every branch resolved or explicitly parked as an open question.
- Do a final pass over the capture file with the user, confirm it matches their intent, and list any flagged open questions at the top.
