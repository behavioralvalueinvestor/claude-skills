# Claude Skills

Four small skills I use every day with Claude Code. Each one is a plain text file of instructions. There is nothing to run and nothing to configure.

## Install

Paste this sentence into Claude Code, either in the terminal or in the Code tab of the Claude desktop app:

> Install the skills from https://github.com/behavioralvalueinvestor/claude-skills: download the repo and copy each folder inside `skills/` into my personal Claude skills folder (`~/.claude/skills`), then list what you installed.

Then quit and restart Claude. To update later, paste the same sentence again.

## What's inside

- **/intent**: Claude restates your goal and the problem you are solving, then waits for your corrections or a "go". Use it before any task where a misunderstanding would cost you an hour.
- **/grill-me**: Claude interviews you about a plan or a decision, one question at a time, and saves every answer to a file in a `brainstorms/` folder. A long interview will outlast Claude's memory of the conversation. The file won't.
- **/handoff**: Claude writes a short document on where the work stands and what comes next, saved to a `handoffs/` folder.
- **/pickup**: A fresh Claude session loads the latest handoff and continues from the next step.

Use /handoff and /pickup as a pair. When a session runs long and Claude starts losing track of earlier decisions, hand off and start fresh.
