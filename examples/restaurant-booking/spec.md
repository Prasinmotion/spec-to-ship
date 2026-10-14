# Restaurant no-show booking app: spec

**Date:** 2026-10-14 · **Source:** conversation (`/client-grill` interview, same day)

## Problem
Diners book a table at peak and don't turn up. The restaurant loses roughly 3–5 tables a night at peak that walk-ins could have filled. Nobody measures this today, so the real figure is unknown.

## Users
- **Owner** (payer): fewer empty peak tables, more bookings and bigger bills.
- **Manager** (signs off on operation): rules staff will trust at peak, and a weekly no-show count.
- **Staff** (user): enter phone bookings mid-call in a few taps, and mark arrivals.
- **Diners** (user): easy reminders, cancelling and rebooking, with no deposits or penalties.

## Goals (measurable)
- Lost tables per peak service: 3–5 (rough; replaced by at least 4 weeks of tracker data) → 1–2, within 3 months of stage 2 launch (date ?).
- Booked tables: ? (Petpooja) → +20%, within 3 months of stage 2 launch (date ?).
- Average bill: ? (Petpooja) → +5%, within 3 months of stage 2 launch (date ?).

Peak means Wednesday to Friday lunch, plus Friday dinner.

## Non-goals
- Deposits, card holds or penalties for no-shows: the client chose soft rules only.
- Making Saturday lunch peak at launch: it's tracked, then reviewed after 4 weeks of data.
- QR waitlist join and the "table ready" WhatsApp message: moved to later, and cut first if the budget is short.
- Food ordering, delivery or takeaway: the app books tables only.

## Constraints
- **Budget:** agreed range (private), build only. The client pays WhatsApp and hosting monthly.
- **Deadline:** no-show tracker within 3–4 weeks, then reminders and rebooking within 2–3 months. Neither date is fixed; a slip means more lost tables.
- **Stage order:** the starting no-show figure must be written down before reminders go live.
- **Messaging:** reminders go through WhatsApp's official business connection. Every message has a "Stop" option.
- **Data:** booked tables and average bill are read from Petpooja.

## Open questions
- Exact budget figures within the ranges: owner (blocks scope and quote).
- Stage 1 start date: owner (blocks all goal dates).
- Booked tables and average bill today, from Petpooja: owner (blocks the two baselines).
- Does giving a number on a call count as WhatsApp agreement? Owner (blocks reminders for phone bookings).
- Does the manager accept soft-only rules and peak approval? Manager (blocks stage 2 sign-off).
- Minimum notice for online bookings, assumed 2 hours: manager (blocks booking rules).
- Staff logins needed, and for which roles: manager (blocks staff screen set-up).
- Still 14 days ahead and groups up to 20 online? Manager (blocks booking rules).
