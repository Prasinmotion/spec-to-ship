# Restaurant no-show booking app: acceptance criteria

**Date:** 2026-10-16 · **Source:** `examples/restaurant-booking/spec.md`

Peak means Wednesday to Friday lunch, plus Friday dinner (from the spec). Example names and numbers below are test data, not client facts.

## S1. Enter a phone booking mid-call

As a **Staff** member, I want to enter a phone booking while the diner is still on the call, so that every booking is in the tracker.
**Serves:** Lost tables per peak service; Booked tables +20%

**AC1.1 (happy)**
- **Given** Thursday lunch has no booking for "Asha", +91 90000 00001
- **When** staff saves a booking for Asha, party of 4, Thursday 13:00, with that number
- **Then** Thursday 13:00 lists one booking for Asha, party of 4, status "Booked", source "Phone"

**AC1.2 (unhappy)**
- **Given** staff has entered name "Asha", party of 4, Thursday 13:00, and no phone number
- **When** staff saves the booking
- **Then** staff sees that a phone number is needed, and no booking is created

**AC1.3 (unhappy)**
- **Given** staff has saved Asha's booking for Thursday 13:00
- **When** staff saves the same booking again within the same call
- **Then** Thursday 13:00 still lists exactly one booking for Asha

**AC1.4 (edge)**
- **Given** the diner gave their number on the call and was not asked about WhatsApp
- **When** staff saves the booking
- **Then** the booking's WhatsApp reminder setting is ? (see Spec gaps)

**AC1.5 (happy) ⚠️ untestable**
- **Given** staff is on a call at peak
- **When** staff enters a booking
- **Then** it takes "a few taps"

## S2. Mark arrivals and no-shows

As a **Staff** member, I want to mark each booking as arrived or no-show, so that the restaurant finally measures its no-shows.
**Serves:** Lost tables per peak service

**AC2.1 (happy)**
- **Given** Asha's booking for Thursday 13:00 has status "Booked"
- **When** staff marks it "Arrived"
- **Then** its status is "Arrived" and Thursday lunch's no-show count is unchanged

**AC2.2 (happy)**
- **Given** Asha's booking for Thursday 13:00 has status "Booked"
- **When** staff marks it "No-show"
- **Then** its status is "No-show" and Thursday lunch's no-show count goes up by 1

**AC2.3 (unhappy)**
- **Given** Asha's booking for Thursday 13:00 has status "Cancelled"
- **When** staff tries to mark it "No-show"
- **Then** staff sees that a cancelled booking can't be a no-show, the status stays "Cancelled", and the no-show count is unchanged

**AC2.4 (unhappy)**
- **Given** Asha's booking was marked "No-show" by mistake
- **When** staff changes it to "Arrived"
- **Then** its status is "Arrived" and Thursday lunch's no-show count goes down by 1

**AC2.5 (edge)**
- **Given** a booking for Saturday 13:00
- **When** staff marks it "No-show"
- **Then** it is counted under Saturday lunch, and not in the peak no-show count

**AC2.6 (unhappy)**
- **Given** Thursday lunch has ended and one booking is still "Booked"
- **When** the service closes
- **Then** that booking is ? (see Spec gaps)

## S3. Weekly no-show count

As the **Manager**, I want a weekly no-show count, so that I can see whether no-shows are falling.
**Serves:** Lost tables per peak service

**AC3.1 (happy)**
- **Given** in week 42 there were 4 no-shows at Wednesday lunch, 3 at Thursday lunch, 5 at Friday lunch and 2 at Friday dinner
- **When** the manager opens the week 42 count
- **Then** it shows those four figures, a peak total of 14 and an average of 3.5 per peak service

**AC3.2 (edge)**
- **Given** week 42 also had 2 no-shows at Saturday lunch
- **When** the manager opens the week 42 count
- **Then** Saturday lunch shows 2 on its own line, and the peak total is still 14

**AC3.3 (unhappy)**
- **Given** in week 42, 6 Thursday lunch bookings were never marked
- **When** the manager opens the week 42 count
- **Then** it shows "6 unmarked" for Thursday lunch, and those 6 are not counted as arrived or as no-shows

**AC3.4 (unhappy)**
- **Given** a staff member is signed in
- **When** they open the weekly count
- **Then** they are ? (see Spec gaps)

## S4. Goal progress against the baseline

As the **Owner**, I want to see each goal's starting figure next to its current figure, so that I know whether the app is paying off.
**Serves:** Lost tables per peak service; Booked tables +20%; Average bill +5%

**AC4.1 (happy)**
- **Given** the tracker has 4 full weeks of marked peak services averaging 4 no-shows each
- **When** the owner opens goal progress
- **Then** the starting no-show figure shows 4 per peak service, with the 4 weeks it came from

**AC4.2 (unhappy)**
- **Given** the tracker has 2 full weeks of data
- **When** the owner opens goal progress
- **Then** it shows "2 of 4 weeks", and no starting no-show figure is recorded

**AC4.3 (happy)**
- **Given** Petpooja reports 310 booked tables and an average bill of ₹1,800 for the starting period
- **When** the owner opens goal progress
- **Then** it shows 310 booked tables (target 372) and ₹1,800 average bill (target ₹1,890), labelled "from Petpooja"

**AC4.4 (unhappy)**
- **Given** Petpooja can't be reached
- **When** the owner opens goal progress
- **Then** the booked tables and average bill show the time they were last read, and no new figure is created or estimated

**AC4.5 (unhappy) ⚠️ untestable**
- **Given** a peak service with 4 no-shows
- **When** the owner opens goal progress
- **Then** it shows the number of "lost tables walk-ins could have filled" for that service

## S5. Book a table online

As one of the **Diners**, I want to book a table online, so that I don't have to call.
**Serves:** Booked tables +20%

**AC5.1 (happy)**
- **Given** it is Monday 10:00 and Thursday 13:00 has space
- **When** a diner books a party of 4 for Thursday 13:00
- **Then** Thursday 13:00 lists the booking with status "Booked" and source "Online"

**AC5.2 (unhappy)**
- **Given** it is Thursday 11:30
- **When** a diner tries to book Thursday 13:00 (90 minutes ahead; minimum notice assumed 2 hours)
- **Then** the diner sees the minimum notice, and no booking is created

**AC5.3 (unhappy)**
- **Given** it is 1 October
- **When** a diner tries to book 16 October (15 days ahead; limit assumed 14)
- **Then** the diner sees the 14-day limit, and no booking is created

**AC5.4 (unhappy)**
- **Given** it is Monday 10:00
- **When** a diner tries to book a party of 21 (limit assumed 20)
- **Then** the diner sees the party limit, and no booking is created

**AC5.5 (unhappy)**
- **Given** Thursday 13:00 is full
- **When** a diner tries to book it
- **Then** the diner sees it is full, and no booking is created. How "full" is set is ? (see Spec gaps)

**AC5.6 (edge)**
- **Given** a diner is completing an online booking
- **When** they confirm it
- **Then** they are not asked for card details, a deposit or a hold (non-goal fence)

## S6. WhatsApp reminder

As one of the **Diners**, I want a reminder before my booking, so that I remember to come or cancel.
**Serves:** Lost tables per peak service

**AC6.1 (happy)**
- **Given** Asha has a Thursday 13:00 booking and has agreed to WhatsApp messages
- **When** the reminder time arrives (? before the booking)
- **Then** one WhatsApp reminder is sent to +91 90000 00001 through WhatsApp's official business connection, and it includes a "Stop" option

**AC6.2 (unhappy)**
- **Given** Asha replied "Stop" to an earlier message
- **When** her next reminder time arrives
- **Then** no WhatsApp message is sent to her, and her booking is unchanged

**AC6.3 (unhappy)**
- **Given** the starting no-show figure has not been recorded (see AC4.2)
- **When** anyone tries to switch reminders on
- **Then** reminders stay off and no reminder is sent (stage order constraint)

**AC6.4 (unhappy)**
- **Given** WhatsApp reports that Asha's reminder was not delivered
- **When** staff open Thursday 13:00
- **Then** Asha's booking still has status "Booked", and staff see ? (see Spec gaps)

**AC6.5 (edge)**
- **Given** Asha has not yet arrived
- **When** her reminder is sent
- **Then** it says nothing about deposits, fees or penalties (non-goal fence)

**AC6.6 (happy) ⚠️ untestable**
- **Given** Asha receives a reminder
- **When** she reads it
- **Then** the reminder is "easy"

## S7. Cancel from the reminder

As one of the **Diners**, I want to cancel from the reminder, so that the restaurant can give my table to someone else.
**Serves:** Lost tables per peak service

**AC7.1 (happy)**
- **Given** Asha has a Thursday 13:00 booking with status "Booked"
- **When** she cancels from the reminder on Wednesday 18:00
- **Then** her booking's status is "Cancelled", Thursday 13:00 has one more free table, and she is not counted as a no-show

**AC7.2 (unhappy)**
- **Given** Asha's booking is already "Cancelled"
- **When** she cancels again
- **Then** she sees it is already cancelled, and nothing else changes

**AC7.3 (unhappy)**
- **Given** it is Thursday 13:30 and Asha's 13:00 booking is still "Booked"
- **When** she tries to cancel
- **Then** the result is ? (see Spec gaps)

**AC7.4 (edge)**
- **Given** Asha cancels 1 hour before her booking
- **When** the cancellation is saved
- **Then** no fee or penalty is charged or mentioned (non-goal fence)

## S8. Rebook from the reminder

As one of the **Diners**, I want to move my booking to another time, so that I don't just drop it.
**Serves:** Booked tables +20%; Lost tables per peak service

**AC8.1 (happy)**
- **Given** Asha has a Thursday 13:00 booking, and Friday 13:00 has space
- **When** she moves it to Friday 13:00 from the reminder
- **Then** Friday 13:00 lists her booking with status "Booked", Thursday 13:00 no longer lists it, and it is not counted as a no-show

**AC8.2 (unhappy)**
- **Given** Friday 13:00 is full
- **When** Asha tries to move her booking there
- **Then** she sees it is full, and her Thursday 13:00 booking is unchanged

**AC8.3 (unhappy)**
- **Given** it is Thursday 12:00
- **When** Asha tries to move her booking to Thursday 13:30 (90 minutes ahead; minimum notice assumed 2 hours)
- **Then** she sees the minimum notice, and her Thursday 13:00 booking is unchanged

## Untestable criteria

| ID | Criterion | Why it can't be tested | Needed to fix it |
|---|---|---|---|
| AC1.5 | Phone booking takes "a few taps" | "A few" has no number, so it can't pass or fail | Owner/manager sets a maximum: taps, or seconds to save a booking |
| AC4.5 | Show "lost tables walk-ins could have filled" | The tracker records no-shows, not whether a walk-in was turned away or would have come | Decide if the goal is measured as no-shows, or add a walk-ins-turned-away count |
| AC6.6 | Reminder is "easy" | "Easy" is not something you can observe | A concrete check, e.g. cancel or rebook in one tap from the message, or a word limit |

## Spec gaps

- Does giving a number on a call count as WhatsApp agreement (spec open question)? Blocks AC1.4, S6 for phone bookings.
- Staff logins: needed, and which roles see what (spec open question)? Blocks AC3.4, and who can mark bookings in S2.
- Minimum notice (assumed 2 hours), 14 days ahead and groups up to 20 all unconfirmed (spec open questions). Blocks AC5.2–5.4, AC8.3.
- What happens to bookings still unmarked when a service ends: stay unmarked, or count as no-shows? Blocks AC2.6, AC3.3.
- How far before the booking is the reminder sent, and is there only one? Blocks AC6.1.
- What do staff see when a reminder isn't delivered, if anything? Blocks AC6.4.
- Can a diner cancel or rebook after the booking time, or within a cut-off before it? Blocks AC7.3.
- How many tables or covers make a slot "full"? The spec gives no capacity. Blocks AC5.5, AC8.2.
- Is the goal "lost tables" the same as no-shows? See AC4.5. Blocks S4.
- What does "peak approval" mean for the manager (spec open question)? It may add a manager story. Blocks stage 2 sign-off.
- Stage 1 start date and Petpooja baselines (spec open questions). Blocks the goal dates and AC4.3 real figures.
