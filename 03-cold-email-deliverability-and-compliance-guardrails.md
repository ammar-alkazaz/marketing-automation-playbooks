# 03. Cold email deliverability and compliance guardrails

## Problem

A cold email program fails quietly. The list was never verified, bounces climb past 5%, the sending domains lose reputation, replies fall toward zero, and the people running it keep increasing volume because volume is the only lever they can see. The fix is a set of guardrails enforced by the system, not by good intentions.

## Infrastructure

- Sending domains separate from the company's main domain. Several domains, several mailboxes each.
- SPF, DKIM and DMARC set on every sending domain and checked monthly.
- Warmup for several weeks before any campaign traffic, and warmup never paused afterwards.
- Strict daily caps per mailbox with rotation across mailboxes. Ramp gradually, never jump.

## Guardrails to enforce in code or platform settings

1. **Verification before upload.** Every address passes an email verifier before it enters a campaign. A second verifier as automatic fallback when the first runs out of credits.
2. **Bounce thresholds judged on a real sample.** Hold the ramp when first-touch bounces reach 3%. Stop sending at 4%. Judge on 700 to 1,000 first emails, never on the first hundred.
3. **Stop on reply and stop on auto-reply.** Any reply ends the sequence for that person.
4. **One organisation, one conversation.** One email per organisation per cooldown window (45 days works for B2B services), a lifetime cap per organisation, and the next contact at the same organisation only after silence.
5. **Opt-out stops the organisation.** If one person says no, nobody else there is emailed. This is both a legal and a reputation rule.
6. **Compliance on every message.** A real sender identity, a truthful subject line, a physical postal address, and a working way to opt out. A plain reply-based line ("a quick no thanks is all it takes") reads human; a marketing unsubscribe header reads like a blast.
7. **Calendar rules.** Business hours in the recipient's time zone, no weekends, public holidays excluded, send times rotated to learn the best slot.
8. **Reply classification.** Interested, meeting, referral and question replies go to a human within two business hours. Opt-outs, bounces, out-of-office and "no longer here" replies are handled automatically and summarised in a weekday report.
9. **Suppression lists.** Current clients, open opportunities and anyone contacted by another campaign inside the cooldown window are excluded before upload.

## Copy rules that protect deliverability

- 50 to 80 words, plain text, one link at most, no images.
- The first line states the specific reason for writing to this organisation.
- An interest question, not a meeting ask, in the first two emails.
- Reading level around grade 5. Short sentences, common words.

## Daily operating routine

- Morning: domain health, bounce rate per mailbox, yesterday's replies by class.
- Weekly: reply rate by sequence step and by send time, spam complaint rate, mailbox rotation check.
- Monthly: DMARC reports, verifier credit balance, suppression list refresh.

## Checks that it works

Bounces held under 3%, mailbox warmup health at 100%, zero complaints from opted-out organisations, and a reply class breakdown that a manager can read in one minute.
