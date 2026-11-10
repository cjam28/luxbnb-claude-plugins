# Claude (Cowork and Claude Code)

Read this when the chat is in Claude. Shared skills stay the same on every host; this file is the Claude UI.

## Workspace

- Reports and scheduled tasks belong in a **Cowork Project**, not a loose chat.
- If this chat is already inside that project, install files **here**. Do not build a zip and do not tell them to create a second project.
- A cloud Cowork project stores files as **project documents**. If there is no folder attached to the Mac, write `reports/` as project documents. Do not search `~/Claude`, `~/Documents`, Desktop, or Downloads.
- Never guess a path. Use the project file root, or ask them to name it.
- Claude Code has no Cowork projects. Prefer Cowork for cloud schedules. If they stay in Claude Code Desktop, a task that must read local files needs **Only on this computer** and the same local folder. A cloud Claude Code task cannot see a Mac-only folder.

## Documents

Put statements, contracts, and other files the schedules must read in the **project**, not only as a chat attachment:

- `reports/statements/` — manager statements
- `reports/contracts/` — agreements
- `reports/contract.md` — rules every run reads
- `reports/schema.md` — record fields

If the host cannot store an empty folder, write a short `reports/statements/README.md` that says to drop files here. Chat uploads do not survive into later scheduled runs.

## Project instructions

You cannot edit project instructions yourself. Pause and give them this block to paste, then wait until they say they added it and to continue:

```
Scope: <group or listings>. Folder: this project, docs under reports/. Time zone <tz>. Targets: <or none>. Management terms: <only what they stated>. Living report: <link or "not created yet">. Read reports/contract.md first. Each task writes only its own reports/data/<tab>/YYYY-MM-DD.json and its own dashboard tab.
```

## Scheduled tasks

Create tasks **inside this project** (`/schedule` or the project's scheduled tasks). Stagger times; avoid :00 and :30.

Interactive Guesty changes: show the change and wait. Never tell them to pick **Always allow** for those.

Scheduled report tasks are different. They only read Guesty and write the living report. After you create them, **stop** and give these steps. Wait for them to say continue:

1. In Claude profile settings, turn on the option that lets scheduled tasks run with connectors without an approval prompt each time (permission mode / bypass for schedules).
2. Open each new task and set its permission mode to **bypass**.
3. Set the model: weekly and other fast checks → **Sonnet** (or the fast model). Income check and monthly briefing → **Opus** (or the strongest model). Do not leave every task on Opus.
4. Confirm each task lists this plugin and the Guesty connector in its tools, plus the dashboard write path. The prompt must stand alone: assistant rules, read-only Guesty, `reports/contract.md`, folder, dashboard link, and the one tab it writes.
5. Return to **this** chat and say continue.

If creating or updating a task fails, say which task failed. Do not claim the briefing date moved if the update was blocked. Do not let the monthly briefing's first run land before they have reviewed the other checks; pause that task if the product allows, and say so if the pause was blocked.

## Orchestrator chat

Tell them this chat is where they change the system later. **Pin it** in the project so they can find it.

## First fire

After the hardening pass, ask permission to run every operational check once now. Do not fire them until they say yes. Review results before the briefing runs.
