---
name: client-brief
description: Rewrite a spec as a short brief for a non-technical client - at most 200 words, no jargon, explaining what the product does for their business and when, and ending with "Decisions we need from you" (usually 3). Use when the user wants a spec turned into a client-facing summary, update, or plain-English brief.
---

Rewrite a **spec** as a brief the client can read in a minute. You are translating, not inventing: every line must trace back to the spec.

## Source

Use, in this order:

1. A file the user names (for example `specs/restaurant-booking.md`).
2. A spec written by `/spec` in the current conversation.

If there is no spec, stop and suggest running `/spec` first.

## Format

```markdown
# <Project name>: what we're building for you

<1–2 sentences: the problem in the client's own words and what it costs them today.>

## What it will do for you
- <business outcome, e.g. "fewer empty tables on Friday nights">

## When
- <milestone>: <date>

## What it won't do (yet)
- <one line per non-goal that the client might expect>

## Decisions we need from you
1. <question>: <why it matters, and by when>
```

## Rules

- **At most 200 words**, headings included. Count before you show it. If it doesn't fit, cut detail, never a decision.
- **No jargon.** No tech terms, acronyms, or internal labels (API, backend, MVP, sprint, user story, integration, metric names). If a reader outside software wouldn't say it, rephrase.
- **Business, not features.** Say what changes for the client (money, time, customers, staff), using the spec's goals and their numbers. Mention a feature only to explain an outcome.
- **When** comes from the spec's deadline and constraints. If the spec gives no date, say so and make it a decision.
- **Decisions we need from you**: usually 3, taken from the spec's open questions that the client owns or that block building. Phrase each as a question they can answer. Skip open questions the team owns.
- Leave out budget figures unless the user asks for them.
- Plain, short sentences. Warm but direct.

## Done

Show the brief with its word count, then save it to `briefs/<project-slug>.md` in the project (create the folder if needed).
