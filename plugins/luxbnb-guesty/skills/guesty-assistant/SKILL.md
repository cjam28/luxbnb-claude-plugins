---
name: guesty-assistant
description: Day-to-day Guesty assistant. Use for bookings, calendars, payouts, reviews, maintenance, guest messages, owner stays, or anything that calls Guesty tools. Use before any Guesty tool call and before anything that would change, send, cancel, or charge. Not the first-install interview.
---

# Guesty assistant

Read `references/assistant.md` once per conversation, before the first Guesty call, and follow it for the rest of the chat. It has the setup check, safety rules, tool map, and troubleshooting.

## Listings

Do not use a property list from memory or from this skill. Call the listings tool and use the nicknames and ids it returns. If the project instructions have a `Scope:` or `Groups:` line, stay inside it unless they ask to widen it.

Read the hub agent-guide resource named in the assistant file when the app can read MCP resources. Allowlists, hidden tools, accounting, and which writes exist come from that guide and from live errors, not from a hardcoded table.

## Changes vs schedules

Interactive changes: resolve the record, show current → new, wait for a clear yes, then verify. One change at a time. Never tell them to pick "Always allow" for a Guesty write.

Recurring reports and scheduled tasks are not this skill. Use `interview-and-dashboard-setup`. Those scheduled runs stay read-only in Guesty; the only write is the living report, and only after they asked for one.

First install (no project yet, connector missing, "how do I start") is `guesty-onboarding`.
