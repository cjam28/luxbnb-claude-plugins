---
name: interview-and-dashboard-setup
description: Interview and dashboard setup for Guesty reports. Use when the user agrees to the kickoff interview, asks for weekly or monthly checks, or wants scheduled owner or PM reports. Sets up one or more living dashboards and scheduled tasks. Does not start by itself after a connection check.
---

# Interview and dashboard setup

Follow `references/recipes.md`. It is the interview, the shared files, the starter checks, and the handover.

If `references/pm-recipes.md` exists, that file is the extra operations library (morning brief, inbox, and similar). Use it when they ask for one of those checks. Where it still says to ask before a scheduled run, ignore that. `references/recipes.md` and the host file win: scheduled report tasks use bypass, and interactive Guesty changes still wait for a yes.

If `guesty-assistant` has not run its setup check in this chat, read that skill's `references/assistant.md`, run the check, and give the tour in two or three lines before the first interview question.

## Host UI

Before you create files or tasks, read the host file for this app (plugin root, sibling of `skills/`):

- Claude → `../../claude/HOST.md`
- ChatGPT or Codex → `../../chatgpt/HOST.md`
- Grok → `../../grok/HOST.md`

Those files say where documents go, how to pause for project instructions, how to set schedule permission and models, and how to pin this chat. Follow them. Do not invent a Mac path.

## Rules that always apply

- Ask one interview question at a time.
- A management fee needs a **rate and a basis**. Do not guess the basis from a bare number.
- Ask how they want listings **grouped** (one combined dashboard, one per listing, or named groups). Do not assume one portfolio row.
- If this chat is already in the project, install there. No zip. No home-directory search.
- Statements and contracts go in the project (`reports/statements/`, `reports/contracts/`), not only in this chat.
- Scheduled task prompts must be complete without a separate project skill. A saved skill is optional. If it fails, continue.
- Interactive Guesty writes wait for a yes. Scheduled report tasks use the host's bypass / unattended mode so connectors run without a prompt. Pause and let them set that, and set models, before you continue.
- After tasks exist, do a hardening pass, then ask before firing every operational check once.
- Tell them to pin this chat and return here to change the system.
