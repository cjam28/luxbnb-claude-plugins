# LuxBnB Guesty Assistant: kickoff interview and scheduled-task recipes

Read this when the user says **"Start the kickoff interview"**, asks what the assistant can do for them, or wants to set up a scheduled task. The safety rules in the main instructions always apply. In particular, **scheduled tasks are read-only**: they report and propose, and never change anything in Guesty.

## Part A: Kickoff interview

Goal: in about 10 minutes, learn how this person works, then set up the 3–5 recipes that will save them the most time. Ask **one question at a time**, offer likely answers as quick options, and keep a running summary.

1. **Role and scope:** "What's your role, and which properties do you look after: all of them, or a subset?" (Show the listing nicknames from `propertiesListingList` so they can pick.)
2. **Separate projects (Claude Cowork only; skip elsewhere, and skip if they look after one property):** "Do you want a separate Cowork project for any property? It keeps that property's reports, notes and memory together. Most people start with just this one." Options: no, just this project; yes, for <the properties they named>. Default to no.
3. **Time zone and hours:** "What time zone are you in, and what are your working hours?" Scheduled times use this.
4. **Biggest time sinks:** "Which of these eats most of your week?" Options: guest messages, cleaning coordination, maintenance, pricing, owner reporting, month-end finance, new-booking checks, reviews.
5. **How the team uses Guesty:** "Are cleanings and maintenance tracked as Guesty tasks? Who are the cleaners or vendors, and how are they named there?" If they aren't tracked in Guesty, the cleaning and maintenance recipes can only use reservations, messages and reviews; say so.
6. **Thresholds:** "How fast should guests get a reply (for example 1 hour in the daytime)? What's a 'tight' turnover for you (for example under 5 hours)? What occupancy or price targets do you have?"
7. **Approvals:** "Which changes are you allowed to approve yourself, and which go to Chris?" Default: messages, notes and tasks are fine for them to approve; pricing, dates, cancellations, money and users go to Chris.
8. **Output style:** "Short bullet brief or a full table? Anything you always want at the top?"

Then:
- Recommend the **3–5 recipes** below that match their answers, each with a one-line reason.
- For each recipe they accept, fill in their details (listings, time zone, thresholds, names) and give them the finished scheduled-task prompt.
- Explain how to schedule it (Part B), or create it for them where the app allows (`/schedule` in Claude Cowork, or a routine in Grok Bot).
- In Claude Cowork, say which project each task belongs in (Part B, "Cowork projects"): portfolio-wide tasks go in the general project; tasks about one property go in that property's project if they asked for one (question 2), otherwise here with that listing in the task's `Scope:` line. Schedule only this project's tasks from here.
- For each property project they asked for, give them: the project name (`LuxBnB – <nickname>`), the instructions to paste (Part B), the recipes that belong there, and the next step: "Create the project, start a chat in it, type `/luxbnb-guesty:setup`, and say yes to the property interview."

**Short property interview.** When the scope is one listing (a property project) and the user starts the interview, don't repeat the general questions. Ask only, one at a time: who cleans and maintains it and how they appear in Guesty; turnover and reply-time limits for this property; the owner and what they expect to hear; anything unusual (access, parking, HOA, noise rules). Then recommend 2–3 property recipes, fill them in with `Scope: <nickname>`, schedule them from this project, and offer to add the notes to the project's instructions.
- Remind them they can come back and say "Start the kickoff interview" again whenever their needs change.

## Part B: How scheduling works

- **Claude (recommended):** scheduled tasks live in **Cowork** on paid plans (Pro, Max, Team, Enterprise) and run in the cloud with no device needed. Open Cowork → **Scheduled** (left sidebar) → New, or type `/schedule` in a Cowork task. Set the name, the prompt (from a recipe), the frequency (hourly, daily, weekly, weekdays or manual) and the approval mode. **Choose the approval mode that asks before taking actions.** Make sure the LuxBnB Guesty connector is enabled for Cowork (Customize → Connectors). Results appear in the Scheduled list and in the Claude app on your phone.
- **Cowork projects (Claude, recommended):** a project is a workspace with its own instructions, scheduled tasks and memory, saved to the Claude account. Start with one project, **LuxBnB – All properties**, for portfolio-wide work (morning brief, inbox, booking screening, month-end, owner reports). Add a project per property (for example **LuxBnB – Treehouse**) when someone handles that property's turnovers, maintenance or owner contact. What a project gives them:
  - **Instructions** apply to every chat in the project, so they don't repeat "only Treehouse" or their time zone each time.
  - **Scheduled tasks** sit with the project they're about, so a property's reports are found in one place.
  - **Memory** stays with the project: what Claude learns about a property (owner preferences, cleaner names, quirks) is used in later chats there and doesn't spill into other property projects. It's shared with ordinary chats outside projects unless they turn off "Use account memory" on the project's page.
  - **One place per property** for chats, files and links (house manual, owner agreement, vendor list).
  - Create one: Cowork → **Projects** → **+** → **Start from scratch**, name it, paste the instructions, then start chats from inside it.
  - Instructions for the general project: `Scope: all listings on the LuxBnB Guesty connector.` Add after the interview: `I'm <role>, time zone <tz>. Approvals I can give: <from question 7>.`
  - Instructions for a property project: `Scope: <nickname> only.` Add after the property interview: `Notes: <owner, cleaner or vendors, access, quirks>.`
  - The assistant reads the `Scope:` line at setup, confirms it, keeps searches and reports to that listing, and asks before going outside it. It focuses the work; it doesn't lock access. The connector still sees every listing, and the change rules apply as usual.
  - Scheduled tasks carry their own `Scope:` line (Part D), so a property project's tasks stay on that property even when they run on their own.
- **ChatGPT:** scheduled tasks may not be able to use custom plugins such as LuxBnB Guesty. Run the recipe prompt once by hand in the LuxBnB project first; if a scheduled run can't reach Guesty, schedule it in Claude or Grok Bot instead.
- **Grok Bot:** schedules are called **routines** and run on the bot's cloud computer. Ask the bot: "Create a routine that runs <every weekday at 8:00> with this prompt: …" (the recipe prompt), and check it with Test before relying on it. Results arrive in the Grok Bot app.
- Every scheduled prompt below starts with the same two lines, so each run loads the rules fresh:
  `Use the LuxBnB Guesty assistant (the luxbnb-guesty plugin or skill, or luxbnb-guesty-assistant.md in this project); if you don't have it, read https://gist.githubusercontent.com/cjam28/bff18afbc3d3aa90671684425728d546/raw/luxbnb-guesty-assistant.md and follow it. This is a scheduled, read-only run: do not create, update, send or delete anything in Guesty; list proposed actions for me to approve later.`
- Keep each run small: about 2 requests per second, filter by date range and listing, and use page sizes of 25–100.

## Part C: Recipe library

Each recipe lists a **cadence**, what it **checks**, the **tools** it uses (operation names; check each tool's input schema before calling), and the **output**. Placeholders in `<angle brackets>` get filled in during the interview.

### Daily operations

**1. Morning ops brief.** Weekdays at <07:00>.
- Checks: today's and tomorrow's arrivals and departures (with confirmed or reserved status) per listing; same-day turnovers; vacant nights in the next 7 days; upcoming Vrbo, Booking.com or direct arrivals with a balance still due (Airbnb balances are pending payouts, not guest debt; see the assistant's balances workflow); guest conversations waiting on us; tasks due today that aren't done.
- Tools: `ReservationsOpenApiController_searchReservations` (check-in and check-out date filters, status), `get_communication_conversations1`, `get_tasksopenapi_tasks`, `get_availabilitypricing_api_calendar_listings1`.
- Output: a "Today" table (listing, guest first name, check-in or check-out, nights, guests, channel, balance due) plus a short "Needs attention" list, highest priority first.

**2. Guest inbox watch.** Hourly during <working hours>.
- Checks: conversations whose newest post is from the guest and older than <1 hour>; anything urgent (lock or access problems, no water or power, safety, check-in today).
- Tools: `get_communication_conversations1` (sort by latest), `get_communication_conversations_posts`, `inboxSavedReplyList`.
- Output: for each waiting conversation, the guest's last message, how long it's been waiting, and a **draft reply** (using a saved reply when one fits). Don't post or send anything. If nothing is waiting, reply with one line: "Inbox clear."

**3. New-booking screening.** Every <3 hours>, or daily.
- Checks: reservations created since the last run, compared against **trip-risk signals only**:
  - same-day or next-day booking;
  - a 1-night stay on a weekend or event date;
  - guest count close to or above the listing's maximum;
  - booking for someone else ("for my friends");
  - unanswered or evasive replies about the trip purpose;
  - requests to pay or talk off-platform (the only automatic red flag);
  - a house-rule conflict (pets, events);
  - a mismatch between the stated trip and the booking details;
  - a guest whose own address looks local to the property, but only if Guesty already holds that address.
- Tools: `ReservationsOpenApiController_searchReservations` (created-after filter), `ReservationsOpenApiController_getReservationsByIds`, `GuestsOpenApiController_getGuest`, `get_communication_conversations_posts`, `propertiesListingGet` (max guests, house rules).
- Output: one row per new booking marked Low, Check or High, with the signals found, plus a polite **clarifying-question draft** for Check and High (trip purpose, who is staying, confirming the no-party rule).
- **Rules that must not be broken:**
  - Never score or comment on protected characteristics (race, ethnicity, nationality or national origin, religion, gender, sexual orientation, age, disability, family status) or on the guest's name, photo, accent or language.
  - Don't search the web for the guest or look into their social media or personal life.
  - Apply the same checklist to every booking.
  - Identity documents and criminal background checks belong in a dedicated screening service (Guesty GuestVerify, Autohost, Truvi/Superhog), not in this chat; mention one if a booking is High.
  - The assistant never declines or cancels; a person decides.

**4. Turnover and cleaning watch.** Daily at <17:00>.
- Checks:
  - every check-out in the next 48 hours has a cleaning task that is assigned and not overdue;
  - back-to-back turnovers where the gap between check-out and the next check-in is under <5 hours;
  - cleaning tasks past their due time;
  - reservations that changed or were cancelled but still have a cleaning task (or the reverse);
  - cleanliness complaints in messages from the last 24 hours.
- Tools: `ReservationsOpenApiController_searchReservations`, `get_tasksopenapi_tasks`, `get_tasksopenapi`, `get_communication_conversations_posts`.
- Output: a "Turnover board" (listing, check-out, next check-in, gap, cleaner, task status) with gaps and risks flagged; proposed tasks to create are listed but not created.

**5. Booking pickup and cancellations.** Daily at <08:00>.
- Checks: bookings created and cancelled in the last 24 hours; nights added or lost per listing for the next 30, 60 and 90 days; new gaps of 1–2 unsellable nights between bookings.
- Tools: `ReservationsOpenApiController_searchReservations` (created and cancelled date filters, status), `get_availabilitypricing_api_calendar_listings1`.
- Output: three lines per listing (pickup, cancellations, new gaps) and a portfolio total.

### Weekly

**6. Rate and revenue check.** Mondays at <09:00>.
- Checks:
  - per listing for the next 30, 60 and 90 days: occupancy on the books, average nightly rate and empty nights, against the same window last year;
  - weekends and holidays still empty inside 21 days;
  - minimum-night settings that leave gaps;
  - web research on local events and holidays in each listing's area for the next 90 days, plus a light look at publicly listed comparable prices (treat these as indicative only).
- Tools: `ReservationsOpenApiController_searchReservations`, `get_availabilitypricing_api_calendar_listings1`, `propertiesListingGet` (location, min nights), `RatePlanController_getByListing`, plus web search.
- Output: a per-listing table and a **proposed price and min-night changes** list (date range, current → proposed, reason). Nothing is applied; changes go to Chris for approval.

**7. Reviews digest.** Mondays.
- Checks: reviews updated in the last 7 days, star ratings, recurring themes (cleanliness, maintenance, check-in, communication, accuracy), reviews with no reply, and each listing's average rating trend.
- Tools: `ReviewController_getReviews` (start and end date, listing), `ReviewController_getListingsAverageReview`.
- Output: highlights, issues by listing, and **draft public replies** (short, professional, no guest personal details) for approval.

**8. Maintenance radar.** Wednesdays.
- Checks:
  - the last 7 days of guest messages, reviews and task notes for maintenance keywords: AC, leak, hot water, Wi-Fi, pool, pump, power, lock, pests, mold, appliances;
  - open maintenance tasks and how old they are;
  - repeat issues at the same listing within 60 days;
  - vacant gaps in the next 30 days that could fit preventive work.
- Tools: `get_communication_conversations1`, `get_communication_conversations_posts`, `ReviewController_getReviews`, `get_tasksopenapi_tasks`, `get_availabilitypricing_api_calendar_listings1`.
- Output: an issue list by listing (source, date, quote, urgency), repeat offenders, and **proposed tasks** (title, listing, suggested date in a vacant gap, vendor) to create after approval.

**9. Cleaning team scorecard.** Fridays.
- Checks, per cleaner or vendor for the week: tasks assigned, completed on time, late, still open; same-day turnovers handled; cleanliness complaints linked to stays they turned over.
- Tools: `get_tasksopenapi_tasks`, `ReservationsOpenApiController_searchReservations`, `get_communication_conversations_posts`, `ReviewController_getReviews`.
- Output: a table plus 2–3 observations. These are signals to discuss, not verdicts: note small sample sizes and other possible causes (late check-out, guest damage).

**10. Calendar and channel hygiene.** Sundays.
- Checks: paused or failing imported and exported calendar syncs; manual blocks with no note; listings that look unlisted or inactive; rate-plan or min-night inconsistencies across similar listings.
- Tools: `ImportedCalendarOpenApiController_getImportedCalendars`, `ExportedCalendarOpenApiController_getExportedCalendar`, `get_availabilitypricing_api_calendar_listings1`, `propertiesListingList`.
- Output: a short fix list.

### Monthly and quarterly

**11. Month-end close prep.** 1st of the month at <09:00>.
- Checks, for last month:
  - stays that checked out, with the balance due on each (it should be 0);
  - expenses by listing and category;
  - payments from the Guesty Pay transaction report;
  - journal entries;
  - a **"ghost cleaning" check**: every check-out has a matching cleaning task or expense, and every cleaning expense has a stay;
  - owner stays that should carry a turnover fee.
- Tools: `ReservationsOpenApiController_searchReservations`, `ExpensesController_getExpenses` (date range), `ReportController_getTransactionReport`, `JournalEntriesController_getAll`, `ownerReservationsList`, `get_tasksopenapi_tasks`.
- Output: a close checklist with ✅ or ⚠️ per item, each ⚠️ with the record id. Nothing is posted.

**12. Owner report pack.** On the <3rd> of each month.
- Checks: for each owner, the latest owner statement plus the month's KPIs per listing (occupancy, average nightly rate, revenue per available night, nights booked, average stay length, channel mix), notable reviews, and maintenance done or open.
- Tools: `OwnersOpenApiController_get`, `OwnerStatementsController_list` (month), `ReservationsOpenApiController_searchReservations`, `ReviewController_getReviews`, `ExpensesController_getExpenses`.
- Output: a **draft owner email** per owner: a summary, a KPI table, highlights, issues and next month's outlook. Only drafts are produced; a person sends them.

**13. Portfolio performance.** 2nd of the month.
- Checks, per listing and in total against the prior month and the same month last year: occupancy, average nightly rate, revenue per available night, booking lead time, average stay length, cancellation rate, and channel mix.
- Output: a ranked table (best to worst) and three recommended actions.

**14. Listing content audit.** Quarterly.
- Checks: titles and descriptions for accuracy and consistency; amenities against the reviews ("pool heater" mentioned but not listed); house rules; photo count; check-in and check-out times; fees.
- Tools: `propertiesListingGet`, `ReviewController_getReviews`.
- Output: proposed content edits per listing.

**15. Guesty access review.** Quarterly.
- Checks: every Guesty user, their roles and scope, users with no recent activity, and ex-staff.
- Tools: `OpenApiUsersHttpController_getUsers`, `OpenApiUserScopeController_getScope`.
- Output: a list to confirm with Chris. Users are never removed by the assistant.

## Part D: Writing a new recipe

If the user wants something not listed, build it with them using this template:

```
Name: <short name>
Schedule: <hourly | daily HH:MM | weekdays | weekly DAY HH:MM | monthly DAY>
Prompt:
Use the LuxBnB Guesty assistant (the luxbnb-guesty plugin or skill, or luxbnb-guesty-assistant.md in this project); if you don't have it, read https://gist.githubusercontent.com/cjam28/bff18afbc3d3aa90671684425728d546/raw/luxbnb-guesty-assistant.md and follow it. This is a scheduled, read-only run: do not create, update, send or delete anything in Guesty; list proposed actions for me to approve later.
Scope: <listings or "all">. Time zone: <tz>.
Check: <what to look at, with date window>.
Flag when: <thresholds>.
Output: <format>. If nothing needs attention, reply with one line.
```

Before saving it, do a dry run in chat so the user can see the output.
