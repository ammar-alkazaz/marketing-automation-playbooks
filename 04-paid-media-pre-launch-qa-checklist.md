# 04. Paid media pre-launch QA checklist

Run this on every flight before the budget goes live. Most wasted spend I have seen came from a step on this list that nobody checked.

## Creative and copy

- [ ] Every asset meets the placement specs (sizes, safe zones, text limits).
- [ ] Brand rules applied (logo position, palette, type) and consistent across the set.
- [ ] Every claim in the copy traced to a verified source. No invented numbers, clients or quotes.
- [ ] Landing page headline matches the ad promise.

## Landing page

- [ ] Loads under three seconds on a phone connection.
- [ ] Form submits on desktop and phone, and the thank-you state appears.
- [ ] Form submission reaches the CRM with the source fields filled.
- [ ] No redirect strips query parameters (see playbook 05 and the tracking-param-checker tool).

## Tracking

- [ ] UTM scheme applied to every ad URL and documented.
- [ ] Google Tag Manager container present and publishing the latest version.
- [ ] GA4 events fire for page view, form start and form submit (check in real time).
- [ ] Google Ads conversion actions fire on the thank-you event, with the gclid present.
- [ ] Meta pixel and conversions verified in Events Manager test events.
- [ ] Call tracking numbers swap correctly on the page.

## Campaign settings

- [ ] Objective and bid strategy match the goal (leads, not clicks).
- [ ] Budget, schedule and geo match the brief.
- [ ] Automated placements and expansions reviewed. Switch off the ones that spend without converting.
- [ ] Negative keyword lists attached (search).
- [ ] Audience exclusions applied (customers, employees, converters).
- [ ] Naming convention applied to campaign, ad set and ad.

## Reporting

- [ ] Weekly scorecard template ready (playbook 06) with the baseline filled in.
- [ ] Alert in place for a broken form (see the form-health-check tool).

## Sign-off

Name, date, and the one thing you could not verify. If that line is not empty, the launch waits.
