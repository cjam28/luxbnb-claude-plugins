---
name: kickoff-and-recipes
description: LuxBnB kickoff interview and library of recurring Guesty reports. Use it when the user says "Start the kickoff interview", asks what the assistant can do or how to get more out of it, wants something done every day or week, or asks for a standard property-management routine even once. Examples: morning arrivals brief, guest inbox check, screening new bookings for risk, cleaning or turnover board, maintenance follow-up, rate or competitor pricing check, reviews digest, owner report, month-end close. Use this skill instead of improvising one of these routines.
---

Follow `references/recipes.md`. Part A is the interview, Part B explains scheduling (Claude Cowork, ChatGPT, Grok Bot routines), Part C is the recipe library and Part D is the template for new recipes.

The safety rules from the `guesty-pm` skill always apply. Scheduled runs are read-only.

When the user is in Cowork and accepts a recipe, offer to create the scheduled task for them with `/schedule`, using the filled-in prompt. Show them the name, the schedule and the prompt first, and remind them to choose the approval mode that asks before actions. Outside Cowork, give them the filled-in prompt and the steps from Part B for their app.
