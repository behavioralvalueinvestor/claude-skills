# Claude Skills

Four small skills I use every day with Claude Code. Each one is a plain text file of instructions. There is nothing to run and nothing to configure.

## Install

Paste this sentence into Claude Code, either in the terminal or in the Code tab of the Claude desktop app:

> Install or update the skills from https://github.com/behavioralvalueinvestor/claude-skills. Download a fresh copy of the repo into a new temporary folder. For each folder inside its `skills/` folder, replace `~/.claude/skills/<same folder name>/` with an exact copy of it: delete that old folder if it exists, then copy the new one so its SKILL.md ends up at `~/.claude/skills/<same folder name>/SKILL.md`. Do not touch any other folder in `~/.claude/skills/`. Then list the full path of every SKILL.md you installed.

Then quit and restart Claude Code or the desktop app, whichever you used. To update later, paste the same sentence again.

## What's inside

- **/intent**: Claude restates your goal and the problem you are solving, then waits for your corrections or a "go." Use it before any task where a misunderstanding would cost you an hour.
- **/grill-me**: Claude interviews you about a plan or a decision, one question at a time, and saves every answer to a file in a `brainstorms/` folder. A long interview will outlast what Claude can hold in one conversation. The file keeps every answer.
- **/handoff**: Claude writes a short document on where the work stands and what comes next, saved to a `handoffs/` folder.
- **/pickup**: A fresh Claude session loads the latest handoff and continues from the next step.

Use /handoff and /pickup as a pair. When a session runs long and Claude starts losing track of earlier decisions, hand off and start fresh.

## Credit

/grill-me, /handoff and /pickup are modified versions of Matt Pocock's skills (https://github.com/mattpocock/skills), used under the MIT license. His license notice is in [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md). /intent is mine.

Everything here is free to use under the MIT license. See [LICENSE](LICENSE).
