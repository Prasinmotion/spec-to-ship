# Week 2 delivery report: Clear Specs

## Shipped

- **Day 1:** Gave an agent a terrible spec on purpose: "Build a booking app for salons… Just start building; don't ask me questions." It made **81 assumptions** and stated none of them.
- **Day 2:** `/client-grill`, my first skill. It asks one question at a time, business before features, and recommends one of three choices each time.
- **Day 2:** Ran the same brief through it: 28 questions, 0 I couldn't answer. 3 of the bad spec's riskiest 5 assumptions turned out to be wrong.
- **Day 3:** A second interview with the same client, now about no-shows: 27 questions and 7 open questions.
- **Day 3:** `/spec`, which turns an interview into a one-page spec with six fixed sections. Its first run is the restaurant no-show spec.
- **Day 6:** `/acceptance-criteria`, which turns a spec into user stories with Given/When/Then checks. Every story needs an unhappy path.

## What didn't work (and how I fixed it)

- **Day 1: "Don't ask questions" didn't remove the questions. It hid them.** The agent also borrowed a city and a cuisine from my other projects without saying so.
  - **Fix:** wrote `/client-grill` the next day, so the questions get asked out loud.
- **Day 1: Changing the brief mid-build** (salons → restaurants) cost a rewrite and a new set of guesses.
  - **Fix:** the grill settles what the product is before anything gets built.
- **Day 2: 3 answers ended as guesses:** the notice period, staff logins and what "Friday" means.
  - **Fix:** carried them into the Day 3 interview as open questions for the manager.
- **Day 3: The public spec showed the client's budget figures.**
  - **Fix:** moved them to private notes. The spec now says "agreed range (private)".
- **Day 6: The `/client-grill` skill lived in a different folder** from the other skills.
  - **Fix:** moved it to `skills/` with the rest.
- **Day 6: Writing the checks found a gap.** Nothing said what happens to a booking nobody marked as arrived or no-show.
  - **Fix:** asked the client. Staff now get a "3 tables not marked" nudge at the end of service, and unmarked bookings don't count either way.
- **`/stakeholder-brief` didn't make it into week 2.**
  - **Fix:** finished it on Wednesday of week 3.

## Learned

- Questions are cheaper than rewrites. 28 questions found what 81 silent assumptions missed.
- Business first changed the product. The real problem wasn't booking a table. It was tables lost at peak.
- An app that passes its own tests can still be the wrong app. Testing shows it works, not that it's right.
- Each step finds gaps the one before missed. The checks caught a question that the interview and the spec both skipped.

## Next (week 3)

- Commit `/stakeholder-brief`, the restaurant brief and the updated stories.
- Get the client's answers to the brief's 4 decisions: start date, Petpooja numbers, WhatsApp agreement on phone bookings, and the exact budget.
- Get the manager's answers on notice period, staff logins, and online group size.
- Add the "corrections after 8:30 pm" question to the ordering-tool notes (carried over from week 1).
