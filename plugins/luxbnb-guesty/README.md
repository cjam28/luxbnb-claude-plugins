# LuxBnB Guesty

A Claude plugin for the LuxBnB property-management team. It works with the LuxBnB Guesty connector (LuxBnB's Guesty account through the MCP hub) and teaches Claude how to work with it safely: reservations, calendar and pricing, the guest inbox, reviews, cleaning and maintenance tasks, owners and finance.

## Install

- **Claude (web, desktop, Cowork):** Customize → Plugins → Add → Add marketplace → `cjam28/luxbnb-claude-plugins`, then install **LuxBnB Guesty**.
- **Claude Code:** `/plugin marketplace add cjam28/luxbnb-claude-plugins`, then `/plugin install luxbnb-guesty@luxbnb`

## Use it

1. Add the connector to your Claude account (once): Customize → Connectors → + → **Add custom connector**, name `LuxBnB Guesty`, URL `https://mcp.christoalto.com/mcp/luxbnb-guesty`, then Connect and sign in with the LuxBnB hub login you received from Chris. It then works in chat, Cowork, claude.ai and the phone app.
2. Type `/luxbnb-guesty:setup`, or just ask a Guesty question ("who checks in tomorrow?").
3. Type `/luxbnb-guesty:interview` to set up scheduled reports in Claude Cowork.

Other commands: `/luxbnb-guesty:brief` (today's ops brief) and `/luxbnb-guesty:inbox` (guests waiting on a reply, with drafts).

Claude reads freely, but shows every change (target, current value → new value, side effects) and waits for your approval before making it. Scheduled reports are read-only.

## Data

Requests go from Claude to `mcp.christoalto.com`, which calls the Guesty Open API with LuxBnB's credentials. The plugin itself stores nothing and contains no credentials.
