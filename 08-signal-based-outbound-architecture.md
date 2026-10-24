# 08. Signal-based outbound architecture

## Problem

Volume outreach treats every organisation the same and burns domains, reputation and goodwill. Signal-based outreach writes only to organisations with a live reason to talk, and personalises the first line with that reason.

## Architecture

```
seed data  ->  identity layer  ->  signal detection  ->  fit scoring
                                                          |
                                                   human approval gate
                                                          |
                            enrichment + two-step verification
                                                          |
                   sequencing (cadence, cooldown, opt-out, compliance)
                                                          |
                       reply handling  ->  CRM / Slack / weekly report
```

### Seed data and identity layer

- Pull the universe once (business listings, registries, public datasets), then scan narrow.
- One record of identity per organisation, every source kept and labelled.
- A match between two sources requires corroboration (postal code or street number, not the name alone).
- Uncertain matches go to a review file for a human or an AI reviewer. Decisions are stored as labels, never overwritten.

### Signal detection

- A signal is a named thing that happened to this organisation recently (a role being hired, funding received, a dated news event, a website or technology change).
- Each signal type has its own evidence rules and its own recency window. A fundraising appeal is not a funding receipt. An about page describing a current employee is not a hiring signal.
- Corroboration can raise a score but never create a signal.

### Fit scoring

A 0 to 100 score from checks that matter to the offer. For a web services offer: outdated CMS, missing SSL, non-responsive layout, thin backlink profile, weak business profile. Weights are written down and versioned.

### Human approval gate

- Every signal type starts gated. It opens only after a minimum number of reviewed decisions at a minimum precision (for example 50 decisions at 85%), and re-arms automatically if precision drops.
- A read-only reviewer (human or AI) labels waiting and retired signals so silent leaks show up. Only a human approves.

### Enrichment and verification

- Find the top decision makers, then verify in two steps: an email verifier, and a check against the organisation's own website that the person still holds the role.
- Vendor disagreements resolve by a written rule, and the losing contact is retired, not deleted.

### Sequencing

- Staggered three-step sequences per person, next person at the organisation only after silence, everything stops on any reply.
- One email per organisation per cooldown window, a lifetime cap, opt-outs stop the whole organisation, postal address on every email.
- Bounce guardrails (hold at 3%, stop at 4%), business hours in the recipient's time zone, holidays excluded.

### Reply handling

- Interested, meeting, referral and question replies to a human within two business hours.
- "No longer here" replies move to the next person automatically after a cooldown.
- Opt-outs, bounces and out-of-office replies summarised in a weekday report.

## Engineering rules

- Versioned releases with automated tests, an adversarial review before each upgrade, and in-place upgrade scripts.
- Secrets in environment files with a rotation script. Never in chat, never in screenshots.
- Health alarms and a daily plan posted to Slack, so the team knows what the system will do today.
- A command manual and a handoff deck, written before the system is considered done.

## What minimal human effort looks like

One person reviews the day's signals with the reviewer's labels as a first pass, writes the signal emails, and audits the retired signals on Fridays. Everything else runs on its own.
