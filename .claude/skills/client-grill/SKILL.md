---
name: client-grill
description: Interview the user about a client product idea, business first, then features, one question at a time, ending with a summary of decisions and open questions. Use when the user wants a client project idea grilled, scoped, or stress-tested before building.
---

<!-- Inspired by Matt Pocock's grill-me skill (mattpocock-skills: grill-me / grilling). -->

Interview the user **relentlessly** about their client's product idea until nothing is left unresolved. Ask **one question at a time**, then wait for the answer before asking the next. Each answer decides what to ask next: dig into vague answers, and follow up on new things the answer raises before you move on.

## Question format

Give every question four choices. Choices A–C are concrete answers that fit this client, with one of them marked as your recommendation and a one-line reason. Choice D is always a free answer in the user's own words.

```
**Q<n>: <question>**

A) <option>
B) <option> ⭐ Recommended: <one-line reason>
C) <option>
D) Something else: tell me in your own words

Reply with A, B, C, or your own answer.
```

The recommendation can be any of A–C. If the user replies with D or something none of the choices cover, take their answer as given and follow up if it's vague.

## Phase 1: Business

Settle the business before you ask about any features. Cover each of these:

1. **Outcome**: which business metric or result this moves for the client, and by how much.
2. **Payer vs user**: who signs off and pays, who actually uses it day to day, and where their needs differ.
3. **Budget**: the amount, what it covers, and how fixed it is.
4. **Deadline**: the date, what drives it, and what happens if it slips.
5. **Launch-day done**: what must be true on launch day for the client to call it a success, in terms you could check.

If the user brings up a feature during Phase 1, note it for Phase 2 and go back to the business question.

## Phase 2: Features

Only once every Phase 1 item is settled, work through features. Test each one against the outcome, the budget and the launch-day definition of done. For each feature, settle:

- who it serves (payer or user) and which outcome it supports
- whether it is **must-have for launch** or can come later
- the riskiest assumption behind it

## Facts vs decisions

Facts are your job. Before you ask a question, check the project's files (notes, reports, earlier specs) and use what's already there. Put only the decisions and the knowledge that lives in the user's head to the user.

## Done

The interview is done when every Phase 1 item has an answer, every feature has a launch priority, and every remaining unknown is written down as an open question with an owner. Then give a summary:

```
## Decisions
- <decision>: <the answer, and why if it was given>

## Open questions
- <question>: <who needs to answer it> (<what it blocks>)
```

Ask the user to confirm the summary before acting on it.
