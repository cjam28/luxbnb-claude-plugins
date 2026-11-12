# LuxBnB Guesty

Guesty assistant for the LuxBnB property-management team: reservations, calendar, inbox, tasks, and scheduled reports.

Clients install **this** repository only (`cjam28/luxbnb-claude-plugins`). Do not add a parent Guesty monorepo as a marketplace.

## Get started

Guesty assistant for the LuxBnB property-management team: reservations, calendar, inbox, tasks, and scheduled reports. Get started: (1) Work inside a Cowork Project — not a loose chat. (2) Connect the LuxBnB Guesty connector if tools are missing (see this repo's README). (3) In that project chat, run /luxbnb-guesty:setup (guesty-onboarding). (4) Then run /luxbnb-guesty:interview (interview-and-dashboard-setup) in the same chat to build reports. (5) Pin that chat and return there for system changes. Drop statements and contracts under reports/statements/ and reports/contracts/ in the project, not only in the chat.

ChatGPT and Grok use the same three skills (`guesty-onboarding`, `guesty-assistant`, `interview-and-dashboard-setup`). Wording for those apps is in the ChatGPT and Grok marketplace catalogs in this repo.

## Install

- **Claude (web, desktop, Cowork):** Customize → Plugins → Add → Add marketplace → `cjam28/luxbnb-claude-plugins`. Private repos ask you to grant the Claude GitHub App. Then install **LuxBnB Guesty**.
- **Claude Code:** `/plugin marketplace add cjam28/luxbnb-claude-plugins`, then `/plugin install luxbnb-guesty@luxbnb`.
- **ChatGPT / Codex:** add this repo as a plugin marketplace (`.agents/plugins/marketplace.json`), then install **LuxBnB Guesty**.
- **Grok:** add this repo as a plugin marketplace (`.grok-plugin/marketplace.json`), then install **LuxBnB Guesty**.

## Connector

Add it once on the account. Name `LuxBnB Guesty`, URL `https://mcp.christoalto.com/mcp/luxbnb-guesty`. The plugin does not ship credentials.

Work in a Project. Run setup, then the interview in that same chat if you want scheduled reports. Pin that chat. Put statements and contracts in the project under `reports/`, not only in the chat.

Interactive Guesty changes wait for a yes. Scheduled report tasks are read-only in Guesty and should use the host's unattended / bypass permission so they can run without a prompt.
