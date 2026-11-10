# Interview and dashboard setup

Read this when the user has agreed to set up recurring reports. Safety rules in the assistant always apply.

Scheduled runs read Guesty and write the living report only. They never change Guesty. Every number comes from Guesty or the user. If something cannot be read, say so. Do not estimate.

Listings come from the connector (`propertiesListingList` or the equivalent). Do not paste a property list from memory.

## Part A: Interview

Ask **one question at a time**.

1. **Priorities.** What should the checks watch? Income and payouts, occupancy and pricing, guest experience, condition, how the manager is doing, operations (arrivals, inbox, tasks). They may pick several.
2. **Grouping.** How should the numbers be shown? Options: one combined view; one dashboard per listing; or named groups (say which listings sit together — by owner, market, or any mix). Default: one combined view that still shows each listing on its own row, plus a total when there is more than one listing. A management company may want several groups. Do not assume "all properties in one project" is the only shape.
3. **Separate projects.** Only if this app has projects (Claude Cowork, ChatGPT). "Do you want a separate project for any group, or keep one project?" Default: one project. Skip on hosts that have no projects.
4. **Time zone and delivery.** What time zone, and when should weekly checks arrive?
5. **Targets.** Occupancy, nightly rate, monthly income, a maintenance budget, or a fixed cost and the day it posts. If they have none, report trends and flag a single cost over 500 in the listing currency. Do not invent targets.
6. **Management terms.** Fee percent **and what it is calculated on**, cleaning or other pass-through fees, notice, what the manager can decide, anything promised in writing. If they give only a number, ask the basis before you use it. Never assume a basis. Only record what they say or what a document shows.
7. **Living report.** One dashboard per group they chose, with a tab per check and a monthly page, instead of a new document every run. Default: yes.
8. **Write-up.** What changed, what to ask the manager, a short plan, or all of those (default).
9. **Tabs.** Starter: Overview, one tab per accepted check, Monthly briefing. They may rename.
10. **Sources.** Besides Guesty: statement files, contracts, email (read-only), a bank feed, an old export. Tell them now: files go in the project under `reports/statements/` and `reports/contracts/`, not only in this chat. Scheduled runs cannot see a chat attachment.
11. **Facts to lock.** Upcoming owner stays, known statement errors, notes already sent, entity or licence facts. No legal or tax advice.
12. **History.** How far back to fill from real check-outs and reviews. Default 12 months, or since listings started if they say so. Never invent past booking pace.
13. **Models.** Fast checks use a fast model (Claude: Sonnet). Income and the monthly briefing use the strongest (Claude: Opus). You will pause later so they can set this on each task. You often cannot set it at create time.

There is no blanket-approval question. Interactive Guesty changes still need a yes each time.

Then:

- Play back a one-screen summary and wait for a yes. If the fee basis is missing, do not lock the summary.
- Recommend 2–4 checks with a one-line reason. If `pm-recipes.md` is present and they asked for operations, include those by name.
- Unless they opted out, do Part B, then Part F, then Part E **in this project**. Show the folder, name, link, schedule, and prompt before creating anything.
- If they are not in a project, stop and use the host file. Do not zip a kit as the default.

## Part B: Where files live

A loose chat cannot hold the shared report. Follow the host file (`claude/HOST.md`, `chatgpt/HOST.md`, or `grok/HOST.md` at the plugin root).

If this chat is already in the project, write files here. Do not search the home directory. Do not offer a zip unless they have no project and ask for a portable copy.

```
reports/contract.md
reports/schema.md
reports/statements/README.md
reports/contracts/README.md
reports/data/<tab>/YYYY-MM-DD.json
reports/briefings/YYYY-MM.json
```

Each task writes only its own `reports/data/<tab>/` file. The monthly briefing reads the others and writes `reports/briefings/`.

Cloud project with no Mac folder: these are project documents. A placeholder README counts as the folder existing.

One project and one file root per group they asked to separate. Do not point two projects at the same files.

## Part C: Starter checks

Use the ones they accepted. Rename tabs if they renamed them.

1. **Weekly pulse.** Next 30/60/90 nights per listing in the group: booked share, empty nights, owner blocks, average rate where Guesty returns it. New, cancelled, or inquiry activity. Do not seed past booking pace.
2. **Guests and reviews.** Recent review average, unanswered reviews, issues worth a look. Confirmation codes only. No guest names in the stored record.
3. **Condition and manager.** Open tasks, repeat issues in reviews or tasks. Expenses only if a statement or tool actually returned them.
4. **Income.** Gross host payout for the period, stays, and a reconciliation row when a statement is in `reports/statements/`. Fee check uses only the rate and basis they locked.
5. **Monthly briefing.** Reads the other tabs since the last briefing. Schedule it a few days after statements usually arrive. If they are unsure, use the 12th and say so. Do not let it run before they have reviewed the other checks once.

If `pm-recipes.md` exists, its numbered recipes stay available for one-off commands (brief, inbox). Scheduling one of them uses the same Part B files and the same task-prompt rules.

## Part D: New checks

A new check needs: name, group, schedule, the tab it owns, the fields it always writes, and a prompt that starts with the lines in Part E. Do not copy another client's listings, fees, or targets into it.

## Part E: Living report and tasks

Do this before you call the setup finished.

1. **Dashboard.** One per group they asked for. Name they choose, or "Owner dashboard" / "Operations dashboard". Overview, one tab per check, monthly briefing. Show the link.
2. **Contract.** Write `reports/contract.md` (Part F).
3. **Project instructions.** Pause. Give the paste block from the host file. Wait until they say continue.
4. **Tasks.** One scheduled task per accepted check, inside this project. Show name, schedule, model you recommend, and the full prompt. Stagger times. Avoid :00 and :30.
5. **Prompt.** Paste this shape into every task. Fill the blanks. The prompt has to work with no extra skill file:

```
Use guesty-assistant from this plugin and follow it. This is a scheduled run: do not create, update, send, or delete anything in Guesty.
Read reports/contract.md first. Folder: <path or "this project's reports/">. Living report: <link>. Scope: <group>.
You write only reports/data/<tab>/YYYY-MM-DD.json and that tab. Read the previous entry first. Reply with status, headline, and the link.
Enable this plugin and the Guesty connector on the task.
```
6. **Permission and models.** You usually cannot set bypass or the model at create time. Stop. Follow the host file's numbered steps (bypass so connectors run without a prompt; Sonnet/fast for weekly checks; Opus/strongest for income and briefing). Wait for continue.
7. **Optional skill.** If the host can save a project skill, you may save one that only repeats the contract (folder, link, tabs, terms). If it fails or the host has no skills, say so in one line and continue. The contract and the task prompts are the source of truth.
8. **Verify.** Read back each task. If an update failed, say which one. Do not claim a date changed when the update was blocked. Pause the briefing until the other checks have been reviewed, or tell them the pause was blocked and what date will actually run.
9. **Hardening.** Contract and schema exist. Statement and contract drop paths exist (placeholder README is enough). Dashboard tabs match the contract. Each prompt names the assistant, the contract, the link, and one tab. Models and bypass match what they confirmed. Open every tab you can; a blank tab or a script error means setup is not done.
10. **First fire.** Ask permission to run every operational check once now. Do not run them until they say yes. Then review. Only then run the briefing once, if they want it now.
11. **Pin.** This chat is where they change the system later. Tell them to pin it.

A dry run that fails to write the tab gets fixed before you add the next task.

## Part F: Contract

`reports/contract.md` holds:

1. Dashboard link, folder, scope or groups, and a table of tab, task, schedule, and file.
2. Write rules: one tab per task; same-day rerun updates that day's file; only a page-refresh task may republish the dashboard page.
3. Where to find statements, in order: `reports/statements/`, then other statement files in the project, then email read-only. Name the file used.
4. How the briefing rolls other tabs up.
5. Owner or operator facts from the interview, dated. Fee rate and basis, verbatim.
6. Which months were seeded, if any.
7. Quirks found while testing the connector.

`reports/schema.md` lists the fields below.

Record fields every tab uses: `runDate`, `status` (`clear`, `attention`, `action`), `headline`, `analysis` (two to four paragraphs), `suggestions` (up to three: title, priority, detail, draft note marked "Not sent yet"), `sourceNotes`. Leave unread fields empty. Never use zero as a stand-in.

Add these when that check is on:

- **pulse:** `windows` (30, 60, and 90 days, per listing: booked percent, last year's booked percent when Guesty returns it, average rate, empty nights, owner-blocked nights), `activity` (new, cancelled, or inquiry: listing, confirmation code, channel, dates, nights, host payout), `openWindows`, `ownerStays`.
- **guests:** per listing, review average of the 25 most recent, the last 90 days, and the 90 days before that; reviews in 7 days; unanswered reviews; `issues` (severity, date, confirmation code, title, short quote, status). No guest names.
- **maintenance:** period, tasks opened and closed, open tasks with age, repeat issues over 90 days, statement period, itemized costs with a flag over the threshold. Keep the listing on each row.
- **income:** period, gross host payout, nights, stays (listing, confirmation code, channel, dates, nights, host payout), whether a statement was found, and one reconciliation row per stay.
- **Briefing:** period, link to the month page, summary figures, fee findings against the locked rate and basis, alerts, and a short history synthesis. Split money by listing when the sources do.

Seed history only if they agreed. Mark seeded rows. Do not seed pulse pace.

### Each later run

1. Read the contract and the previous record for this tab.
2. Gather only from the named sources.
3. Write one record, to this tab only.
4. If something cannot be read, say so, and still write the record.
5. Reply in a few lines: status, headline, link.

Draft notes are never sent for them.
