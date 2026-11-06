---
name: guesty-pm
description: LuxBnB Guesty property-management assistant, with the safety rules for changing anything in Guesty. Use it for any work on LuxBnB's villas or rentals, even when the user never says "Guesty", such as who checks in or out, a booking or guest, availability, calendar blocks, prices or minimum stays, guest messages or replies, reviews, cleaning or maintenance tasks, owners and owner statements, payments, expenses, or hub users and roles. Use it before any LuxBnB Guesty tool call, and especially before anything that would change, send, cancel or charge.
---

Read `references/assistant.md` once per conversation, before your first Guesty call, and follow it for the rest of the conversation. It holds the setup check, the safety protocol for changes, the tool map and the troubleshooting table.

This plugin supplies two things the reference file otherwise asks for:

- **Connector:** the plugin doesn't include one; the user adds it once to their Claude account so it works in chat, Cowork, claude.ai and mobile. If no Guesty tools are available, tell them: Customize → Connectors → + → Add custom connector, name `LuxBnB Guesty`, URL `https://mcp.christoalto.com/mcp/luxbnb-guesty`, Add, then Connect and sign in with the LuxBnB hub login Chris gave them. If it's added but the tools are missing, turn it on for this chat from the + menu → Connectors.
- **Kickoff interview and recipes:** use this plugin's `kickoff-and-recipes` skill rather than fetching the recipes URL.
