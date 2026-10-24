# 02. Speed-to-lead workflow

## Problem

Research on lead response has pointed the same way for years. The odds of qualifying a lead drop sharply after the first few minutes, and most companies take hours. The fix is not a faster salesperson, it is a workflow that makes the first touch automatic.

## Design rules

- First touch within one minute, by machine, with a human following inside the hour.
- The first message references what the lead asked for. A generic "thanks for your interest" is a wasted touch.
- Every step branches on behaviour (replied, booked, silent) and stops the moment a human takes over.
- Working hours and time zones are respected. A 2 AM SMS loses the lead.

## The sequence

| Minute | Step | Branch |
|--------|------|--------|
| 0 | Internal alert to the owner with source, score and the lead's answers | |
| 0 | SMS to the lead confirming receipt and naming the next step | Reply stops the sequence and creates a task |
| 1 | Call task created for the owner, due in 15 minutes during working hours | Booked call stops the sequence |
| 5 | Email with one specific line about the lead's stated issue and a booking link | |
| Day 1 | Second call attempt task, SMS with the booking link | |
| Day 2 | Email with a short proof point relevant to the lead's issue | |
| Day 4 | Final SMS, interest question, no pressure | Silence moves the contact to the long nurture list |

## Build notes (GoHighLevel, but the shape is the same anywhere)

- Use the contact's stated preferred call time to schedule the call task instead of a fixed delay.
- Put the stop conditions on the workflow itself (reply, booked, stage moved), not on the individual steps.
- Suppress the sequence for existing customers and for contacts in an open opportunity.

## Checks that it works

- Time-to-first-contact, measured from form submission to first SMS and to first human call.
- Share of leads reached within 15 minutes during working hours.
- Booked call rate by source, so a weak intake point shows up quickly.
