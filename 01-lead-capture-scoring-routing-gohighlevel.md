# 01. Lead capture, scoring and routing in GoHighLevel

## Problem

Leads arrive from several places (a landing page form, a Meta instant form, the website contact form), land in inboxes, get copied into the CRM by hand and called whenever someone gets to them. Nobody can say which campaign produced which lead, and sales spends time on leads with no budget or timeline.

## Design rules

- Every intake point writes to the same CRM contact with the same fields, including the source (campaign, ad set, ad, gclid or fbclid, UTM parameters).
- Validity checks run before anyone is notified. Disposable email domains, missing phone numbers, obvious spam and duplicate submissions get tagged, not called.
- Scoring is simple and visible. Five to eight fields, each worth points, with the thresholds written where sales can read them.
- Routing is a rule, not a decision. Score above the threshold creates a pipeline opportunity and a call task; below it goes to a nurture sequence.
- Every step leaves a tag, so the funnel can be reported from the CRM alone.

## Build steps

1. **Fields.** Create custom fields for source, campaign, ad set, ad, click id, UTM source, medium and term, plus the qualification answers you will score (issue, timeline, budget range, role, preferred call time).
2. **Intake points.**
   - Landing page form (WordPress or any builder) posts to a GoHighLevel inbound webhook. Carry the click id and UTM parameters in hidden fields.
   - Meta instant form connects through the native Facebook integration. Redesign the form as a qualification layer, with the same questions you score.
   - Website contact form posts to the same webhook with a different source value.
3. **Validity workflow.** Trigger on contact created. Check email format and disposable domains, phone format, duplicate within 30 days. Tag `valid` or `review`.
4. **Scoring workflow.** Trigger on tag `valid`. Add points per answer (for example timeline within 30 days +30, budget stated +25, decision maker role +20, specific issue described +15, call time given +10). Write the total to a score field.
5. **Routing workflow.** Score at or above the threshold creates an opportunity in the pipeline stage `New lead`, assigns the owner, creates a call task, sends the speed-to-lead steps (see playbook 02) and posts an alert with the source on it. Below threshold enters the nurture sequence and is tagged `nurture`.
6. **Reporting fields.** Add stage-change timestamps so time-to-first-contact and time-to-qualified can be reported.

## Checks that it works

- Submit a test lead from each intake point with a fake click id and confirm the id appears on the CRM contact.
- Submit a known-bad lead (disposable email) and confirm it is tagged `review` and nobody is alerted.
- Pull the pipeline report after a week. Every opportunity should show its source. If any are blank, an intake point is leaking.

## Handoff

Document the field list, the point values, the thresholds and the owner of each workflow in one page. Sales should be able to change a point value without asking a marketer.
