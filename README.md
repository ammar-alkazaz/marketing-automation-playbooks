# Marketing Automation Playbooks

The systems I build for lead generation and marketing operations, written as playbooks you can copy. Each one states the problem, the design rules, the build steps and the checks that tell you it is working.

Everything here is rebuilt from scratch and kept generic. Client work is under NDA, so there are no client names, no client data and no copied code.

| # | Playbook | Use it when |
|---|----------|-------------|
| 01 | [Lead capture, scoring and routing in GoHighLevel](01-lead-capture-scoring-routing-gohighlevel.md) | Forms land in inboxes and sales calls leads blind |
| 02 | [Speed-to-lead workflow](02-speed-to-lead-workflow.md) | First contact takes hours and leads go cold |
| 03 | [Cold email deliverability and compliance guardrails](03-cold-email-deliverability-and-compliance-guardrails.md) | Bounces climb, replies fall, nobody knows why |
| 04 | [Paid media pre-launch QA checklist](04-paid-media-pre-launch-qa-checklist.md) | A campaign goes live and the tracking was never tested |
| 05 | [Attribution and tracking audit](05-attribution-and-tracking-audit.md) | The ad platform and the CRM disagree on lead counts |
| 06 | [Weekly marketing scorecard](06-weekly-marketing-scorecard-template.md) | Management asks what the budget bought |
| 07 | [Content system templates](07-content-system-templates.md) | Founder content depends on one person's memory |
| 08 | [Signal-based outbound architecture](08-signal-based-outbound-architecture.md) | Volume outreach is burning domains and reputation |

## Tools that go with them

- [tracking-param-checker](https://github.com/ammar-alkazaz/tracking-param-checker) checks that gclid, fbclid and UTM parameters survive a redirect chain (playbooks 04 and 05).
- [form-health-check](https://github.com/ammar-alkazaz/form-health-check) runs daily and alerts when a landing page or its form breaks (playbooks 04 and 05).

## Principles behind all of them

1. Measure before opinions. Fix tracking first, then judge the campaign.
2. Put the rules in the system, not in a person's head. Cadence, cooldowns, opt-outs and caps belong in code or workflow settings.
3. Humans approve, machines execute. Every automation ships with an approval gate and expands only when its precision is proven.
4. Write it down the day it is decided. Every system here leaves with a runbook, so the next person can run it without me.
5. Nothing fabricated. Claims, proof points and numbers come from a verified fact bank.
