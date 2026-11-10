---
name: guesty-onboarding
description: First-install guide for a Guesty plugin. Use when the user just installed the plugin, runs setup, or asks how to start. Confirms they are in a Project, checks the connector, and hands off to interview-and-dashboard-setup. Does not build dashboards or scheduled tasks itself.
---

# Guesty onboarding

This skill is first install only. Day-to-day Guesty questions use `guesty-assistant`. Reports and schedules use `interview-and-dashboard-setup`, and only after the user agrees.

Read `references/assistant.md` once and run its setup check before anything else.

## 1. Workspace

Detect the app. Host notes sit two levels up from this file, next to `skills/` (`../../claude/HOST.md` and the same for the other apps):

- Claude → `../../claude/HOST.md`
- ChatGPT or Codex → `../../chatgpt/HOST.md`
- Grok → `../../grok/HOST.md`

If you cannot tell, ask which app they are in and read that file.

You must be in a **Project** (Claude: a Cowork project chat; ChatGPT: a Project; Grok: a bot workspace they will keep). If this chat is loose:

1. Stop.
2. Give the host file's steps to open or create a project.
3. Tell them to start a **new chat inside that project** and run setup again.

If this chat is **already** in the right project, stay here. Do not search the computer for a folder. Do not build a zip. Do not tell them to create another project and paste a kit into it.

## 2. Connector

If Guesty tools are missing, give only the connect steps in `references/assistant.md` for this app. Stop until tools exist. Then run the setup check again.

When it is Ready, list the listings the connector actually returned. Do not invent properties.

## 3. Tour and handoff

Give the short tour from the assistant file. Then say, in your own words:

- This chat is the one to come back to for changes. **Pin it** in the project (Claude), the project list (ChatGPT), or the Library (Grok).
- Interactive Guesty changes always wait for a yes. Never pick "Always allow" for those.
- Reports are a separate step. They do **not** start automatically.

Ask whether to start interview and dashboard setup **in this same chat**. If they say yes, or they run the interview command, load `interview-and-dashboard-setup` and follow it. If they say no, stop. Later questions about bookings, money, or stays use `guesty-assistant`.
