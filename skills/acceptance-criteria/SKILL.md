---
name: acceptance-criteria
description: Read a spec, break it into user stories, and write Given/When/Then acceptance criteria for each. Every story gets at least one unhappy path, and any criterion that can't be tested is flagged. Use when the user wants stories, acceptance criteria, Gherkin, or testable checks written from a spec.
---

Turn a spec into **user stories with Given/When/Then acceptance criteria**. You are deriving, not inventing: every story must trace back to a line in the spec.

## Source

Use, in this order:

1. A file the user names (for example `specs/restaurant-booking.md`).
2. A spec written by `/spec` in the current conversation.
3. A single file in `specs/`, if there is exactly one.

If there is no spec, or it has no **Users** and **Goals**, stop and suggest running `/spec` first. Don't write stories from guesses.

## Breaking the spec into stories

- One story per thing a **user** (from the spec's Users section) needs to do or know. Use their role name exactly as the spec does.
- Each story serves at least one **Goal**. Name it in the `Serves:` line. A story that serves no goal doesn't belong; leave it out.
- **Non-goals are fences.** Never write a story for a non-goal. If a story brushes against one, add a criterion that proves the system *doesn't* do it.
- **Constraints become criteria**, not stories. A deadline doesn't get a story; a "must work offline" or "data stays in the EU" constraint gets a criterion in each story it touches.
- Keep stories small: if a story needs more than 6 criteria, split it.

## Format

```markdown
# <Project name>: acceptance criteria

**Date:** <YYYY-MM-DD> · **Source:** <spec file>

## S1. <short title>

As a **<role>**, I want <capability>, so that <outcome>.
**Serves:** <goal from spec>

**AC1.1 (happy)**
- **Given** <starting state, with concrete values>
- **When** <one action>
- **Then** <observable result, with concrete values>

**AC1.2 (unhappy)**
- **Given** ...
- **When** ...
- **Then** ...

## Untestable criteria

| ID | Criterion | Why it can't be tested | Needed to fix it |
|---|---|---|---|

## Spec gaps

- <question the stories raised that the spec doesn't answer>: <which story it blocks>
```

## Rules

### Every story has at least one unhappy path

Label each criterion `(happy)`, `(unhappy)` or `(edge)`. A story with no `(unhappy)` criterion is not finished. Look for:

- **Bad input**: missing, malformed, too long, wrong type.
- **Not allowed**: wrong role, not signed in, someone else's data.
- **Conflict or limit**: already taken, sold out, over a quota, past a deadline.
- **Dependency fails**: payment declined, SMS not delivered, network down, third party slow.
- **User changes their mind**: cancels, goes back, submits twice.
- **Nothing happens**: a step is skipped, a timeout passes, a record is left unfinished.
- **Our own user gets it wrong**: staff or admin error that needs undoing.

The unhappy **Then** must say what the user sees *and* what state the system is left in (for example "no booking is created", "the card is not charged").

### Every criterion must be testable

A criterion is testable when a tester who has never seen the spec could run it and get a clear pass or fail. Check each one:

- **One action in When.** Two actions means two criteria.
- **Concrete values.** "A party of 4 at 19:30", not "a booking". Numbers, not "fast", "many", "large".
- **Observable Then.** Something a person or a test can see: a message, a record, a status, an email sent. Not "the user is happy" or "it works correctly".
- **No vague words**: fast, easy, intuitive, user-friendly, seamless, appropriate, robust, secure, reasonable, etc. Replace them with a number or a named check, or flag the criterion.

Write the criterion anyway if it can't be made testable, then **flag it**: add `⚠️ untestable` after its label and a row in the **Untestable criteria** table saying why and what's needed (usually a number or a decision from the client). Never silently drop it, and never invent the missing number.

### Stay inside the spec

- If writing a criterion needs a fact the spec doesn't give (a limit, a timeout, a message, a rule), use `?` in that slot and add a line under **Spec gaps**.
- Spec **Open questions** that affect a story go under **Spec gaps** too, naming the story they block.
- No UI design, no implementation detail (tables, endpoints, frameworks). Describe behaviour only.

## Check before showing

Go through the output and confirm:

- [ ] Every story has a `Serves:` goal from the spec.
- [ ] Every story has at least one `(unhappy)` criterion.
- [ ] Every criterion has exactly one When and an observable Then.
- [ ] Every flagged criterion has a row in **Untestable criteria**, and every row matches a flagged criterion.
- [ ] No story covers a non-goal.

Fix anything that fails before you show it.

## Done

Show the stories, then save them to `specs/<project-slug>-acceptance.md` next to the spec (create the folder if needed). End with a short count: stories, criteria, unhappy paths, untestable criteria, spec gaps. Ask the user to resolve the untestable criteria and spec gaps before building starts.
