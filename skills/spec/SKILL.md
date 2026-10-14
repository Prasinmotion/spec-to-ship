---
name: spec
description: Turn a client-grill interview (or the current conversation) into a one-page spec with exactly six sections - Problem, Users, Goals (measurable), Non-goals, Constraints, Open questions. Refuses to go past one page and says the scope is too big instead. Use when the user wants a spec, brief, or one-pager written from an interview, notes, or discussion.
---

Write a **one-page spec** from what has already been decided. You are summarising, not inventing: every line must trace back to the source.

## Source

Use, in this order:

1. A file the user names (for example `notes/client-skill-01.md`).
2. A `/client-grill` interview in the current conversation, using its **Decisions** and **Open questions** summary.
3. The rest of the current conversation.

If none of these has enough to fill **Problem**, **Users** and **Goals**, stop and suggest running `/client-grill` first. Don't fill gaps with guesses.

## Format

Exactly these six sections, in this order, with these headings. No other sections, no intro, no appendix.

```markdown
# <Project name>: spec

**Date:** <YYYY-MM-DD> · **Source:** <file or "conversation">

## Problem
<2–4 sentences: whose problem, what it costs them today, why now.>

## Users
- **<role>** (<payer / user / both>): <what they need from this>

## Goals (measurable)
- <metric>: <baseline> → <target> by <date>

## Non-goals
- <thing this will not do>: <one-line reason>

## Constraints
- **Budget:** <amount and what it covers>
- **Deadline:** <date and what drives it>
- <other hard limits: tech, legal, people, data>

## Open questions
- <question>: <owner> (blocks <what>)
```

## Rules

- **Goals must be measurable.** Each goal has a metric, a baseline, a target and a date. If the source doesn't give a number for one of these, write the goal anyway with `?` in that slot and add an open question asking for it. A goal like "customers love it" is not a goal; turn it into an open question.
- **Non-goals come from the source**: features pushed past launch, ideas rejected in the interview, and the obvious neighbours the client didn't ask for (for example ordering food when the app books tables). Never empty.
- **Assumptions are open questions.** Anything the source marks as assumed or unconfirmed goes under Open questions with an owner, not into the other sections as fact.
- **No features list.** Features belong in the build plan. Mention one only where it is needed to state a goal or non-goal.
- Plain, short sentences. One bullet, one idea.

## Hard limit: one page

One page means **at most 500 words and 60 lines**, counting headings. Check this before you show the spec.

If it doesn't fit, **don't trim content to squeeze it in, and don't show a cut-down spec.** Say the scope is too big instead:

```
⚠️ Scope too big for one page (<n> words / <n> lines, limit 500 / 60).

Biggest sections: <section> (<n> words), <section> (<n> words)

Suggested split:
1. <smaller spec>: <what it covers>
2. <smaller spec>: <what it covers>
```

Then ask which part to spec first. Tightening wording is fine; dropping a goal, user, constraint or open question to make it fit is not.

## Done

Show the spec, then save it to `specs/<project-slug>.md` in the project (create the folder if needed). Ask the user to confirm it, and list any open questions that block building.
