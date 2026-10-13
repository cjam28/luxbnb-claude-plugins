---
name: guesty-pm
description: LuxBnB Guesty property-management assistant, with the safety rules for changing anything in Guesty. Use it for any work on LuxBnB's villas or rentals, even when the user never says "Guesty", such as who checks in or out, a booking or guest, availability, calendar blocks, prices or minimum stays, guest messages or replies, reviews, cleaning or maintenance tasks, owners and owner statements, payments, expenses, or hub users and roles. Use it before any LuxBnB Guesty tool call, and especially before anything that would change, send, cancel or charge.
---

Read `references/assistant.md` once per conversation, before your first Guesty call, and follow it for the rest of the conversation. It holds the setup check, the safety protocol for changes, the tool map and the troubleshooting table.

This plugin supplies two things the reference file otherwise asks for:

- **Connector:** the plugin bundles it. If no Guesty tools are available, tell the user to open Customize → Plugins → LuxBnB Guesty → Connectors tab → Connect, and sign in with the LuxBnB hub login Chris gave them. If they also added the same URL as a separate custom connector earlier, they should remove that one (Customize → Connectors) so the tools aren't listed twice.
- **Kickoff interview and recipes:** use this plugin's `kickoff-and-recipes` skill rather than fetching the recipes URL.
