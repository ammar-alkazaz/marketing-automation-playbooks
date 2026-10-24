# 05. Attribution and tracking audit

## Problem

The ad platform reports fewer conversions than the CRM receives, or the CRM shows leads with no source. Optimisation then runs on partial data, and budget decisions are guesses.

## Audit steps

1. **Map the click path.** Ad click, any redirect, landing page, form, thank-you page, CRM record. Write down every hop.
2. **Follow the parameters.** Open an ad URL with test parameters (`gclid=TEST123&utm_source=test`) and confirm they survive every hop. Redirect rules, trailing slash rewrites, www to non-www, http to https and plugin redirects all strip parameters more often than people expect. The `tracking-param-checker` tool does this automatically.
3. **Check the form carries them.** Hidden fields for click ids and UTM parameters, populated from the URL on page load and sent with the submission.
4. **Check the CRM stores them.** The contact record shows the campaign and click id. If not, the webhook mapping is missing a field.
5. **Compare the counts.** Platform conversions, GA4 events, form submissions, CRM contacts for the same seven days. Each gap points at one hop.
6. **Fix the biggest gap first.** Usually the redirect or the hidden fields.
7. **Re-baseline.** After the fix, treat the following weeks as the new baseline. Earlier numbers were under-counted, not worse.

## What to report

- Before and after counts for each hop.
- The mechanism that was broken and the fix.
- Which earlier decisions were made on bad data and whether they should be revisited.

## Keep it fixed

- A daily automated check of the landing page and form (see the form-health-check tool).
- The pre-launch checklist (playbook 04) on every new flight.
- A weekly glance at the share of CRM leads with an empty source field. It should be close to zero.
