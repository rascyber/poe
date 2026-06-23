# Yamato Google API Key Disclosure PoC

## Purpose

This directory contains a deployment-ready, disclosure-safe static HTML proof-of-concept for a suspected unrestricted Google Maps / Google Cloud API key exposure in a Yamato asset.

The PoC is designed to demonstrate business impact through local simulation and explicit, low-volume manual validation. It does not contain a real secret, does not send API requests on page load, and does not run bulk validation.

## Files

- `index.html` - Bootstrap-based single-page PoC report with simulation controls, manual key entry, live map rendering, and a valid API findings table.
- `assets/` - Optional screenshots or visual assets that are safe to publish.
- `evidence/` - Redacted evidence intended for disclosure packages.
- `reports/YAMATO_API_KEY_DISCLOSURE_REPORT.md` - Bug bounty report template.

## Open Locally

Open `index.html` directly in a browser:

```text
yamato/google-api-key-poc/index.html
```

No build tools are required.

## Deploy as Static HTML

Any static file host can serve this directory. Examples include GitHub Pages, Netlify, Vercel static output, S3 static hosting, or an internal evidence portal.

Deploy the folder:

```text
yamato/google-api-key-poc/
```

Keep raw evidence and unredacted secrets out of public hosting targets.

## Evidence to Attach

Attach only owner-approved, redacted evidence such as:

- Screenshot of the affected Yamato asset or static source location.
- Redacted scanner output showing a Google Cloud API key finding.
- Redacted browser source excerpt or mobile package excerpt.
- Google Cloud console screenshots showing whether application restrictions, API restrictions, quotas, budgets, and alerts are configured.
- Billing or quota observations approved by the program owner.

Do not attach raw secrets, private customer data, production logs, or unapproved live API responses.

## Valid API Findings Table

The validation findings table documents which Google Maps Platform APIs appear enabled for the exposed key.

- A `✅` status means a single authorized validation showed the API accepted the key.
- A `❌` status means the API rejected the key, the request failed, or the API is blocked for the current origin.
- A `⏳` status means the API was not tested.
- Researchers must not perform high-volume checks, loops, or quota-draining validation.
- Evidence must redact the full key in screenshots, copied summaries, exported JSON, and reports.
- Use screenshots of the table, status panel, and rendered map when submitting evidence.

The browser PoC supports manual checks only. Some REST-style Google endpoints may be blocked by browser CORS; in that case, the table provides a redacted equivalent `curl` command for owner-approved validation outside the browser.

## Redacting Secrets

Replace the key body with a stable placeholder:

```text
[REDACTED_GOOGLE_API_KEY_PLACEHOLDER]
```

If you need to correlate the same secret across screenshots, retain only a short non-sensitive prefix/suffix pattern approved by the program, for example:

```text
[REDACTED_GOOGLE_API_KEY_ENDING_ABCD]
```

Never commit `.env`, `*.key`, `secrets/`, or `evidence/raw/` content.

## Safety Boundaries

- Do not perform live abuse of any API key.
- Do not send quota-draining requests.
- Do not validate by making unauthorized Google Maps or Google Cloud API calls.
- Do not run all checks automatically or loop requests.
- Run only single manual checks that are authorized by the program rules.
- Do not include real secrets in this repository.
- Use redacted key display only in all evidence.
- Submit sensitive evidence only through the authorized disclosure channel.

## Suggested Bug Bounty Report Wording

```text
I identified a Google Maps / Google Cloud API key exposed in a Yamato asset. The submitted proof-of-concept is intentionally disclosure-safe and does not perform live exploitation or quota-consuming requests. The risk is that an unrestricted key may be reused by unauthorized third parties, causing overbilling, service abuse, reconnaissance, and reputational impact depending on enabled APIs and configured restrictions.

Please confirm whether the key is restricted by application, API allowlist, quota, and billing controls. I recommend rotating the exposed key, applying strict restrictions, reviewing related assets for additional leaked secrets, and enabling budget and quota alerts.
```
