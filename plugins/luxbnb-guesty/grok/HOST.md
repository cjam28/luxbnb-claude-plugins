# Grok

Read this when the chat is in Grok or Grok Bot. Shared skills stay the same; this file is the Grok UI.

## Workspace

- Routines run in the cloud. Files that must still be there next time go in `/workspace`, not only in the chat and not only on their computer.
- Use one folder, for example `/workspace/guesty/`, with `reports/` inside it. Do not put passwords or tokens there.
- Do not search their Mac for a folder. If they already have a workspace, install into it.

## Documents

Statements and contracts go in that workspace folder:

- `reports/statements/`
- `reports/contracts/`
- `reports/contract.md`

## Dashboard

Ask for one Page and **pin it in the bot's Library**. Routines update that page. They do not make a new page per run. If Pages is missing, the JSON files are the report.

## Routines

Create one routine per check. Its instruction names the folder, the page, the contract, and the one file it writes. It must be readable without a separate skill.

Pause after creating them:

1. Set weekly checks to a faster model and the income check plus briefing to the strongest model, if routines allow a model.
2. Run Test only after they agree.
3. Come back to this chat and say continue.

Interactive Guesty changes still wait for a yes.

A saved skill that repeats the contract is optional. If saving a skill fails, continue. The contract and the routine text are the source of truth.

## This chat

Tell them this chat is the place to change the system later, and to pin it if they can.

Ask before firing every routine once to test.
