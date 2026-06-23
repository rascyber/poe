# Yamato Google API Key Disclosure PoC

## Purpose

This directory contains a deployment-ready, disclosure-safe static HTML proof-of-concept for a suspected unrestricted Google Maps / Google Cloud API key exposure in a Yamato asset.

The PoC is designed to demonstrate business impact through local simulation only. It does not contain a real secret, does not load Google API scripts, and does not send quota-consuming API requests.

## Files

- `index.html` - Bootstrap-based single-page PoC report with local-only simulation controls.
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
- Do not include real secrets in this repository.
- Use the HTML buttons for local simulation only.
- Submit sensitive evidence only through the authorized disclosure channel.

## Suggested Bug Bounty Report Wording

```text
I identified a Google Maps / Google Cloud API key exposed in a Yamato asset. The submitted proof-of-concept is intentionally disclosure-safe and does not perform live exploitation or quota-consuming requests. The risk is that an unrestricted key may be reused by unauthorized third parties, causing overbilling, service abuse, reconnaissance, and reputational impact depending on enabled APIs and configured restrictions.

Please confirm whether the key is restricted by application, API allowlist, quota, and billing controls. I recommend rotating the exposed key, applying strict restrictions, reviewing related assets for additional leaked secrets, and enabling budget and quota alerts.
```
