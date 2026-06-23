# Yamato API Key Disclosure Report

## Summary

A Google Maps / Google Cloud API key appears to be exposed in a Yamato-controlled asset. This report template is structured for responsible disclosure and uses redacted placeholders until the final evidence package is prepared.

## Context

Leaking secrets, passwords, and API keys can cause loss of confidentiality, integrity, availability, reputational damage, legal consequences, and overbilling. The severity depends on whether the key is restricted by application, API allowlist, quota, billing controls, and monitoring.

## Case Study: $450,000 Google Cloud API Key Compromise

A public case involving a translation app reported a Google Cloud API key compromise that led to about $450,000 in charges over roughly 1.5 months. The app reportedly had a normal monthly cost near $1,500, while around 19 billion translation characters were processed without the owner knowing. The owner described limited warning and partial credits, not a full refund. This case study is included only to show plausible financial impact from exposed and abused cloud keys; it is not evidence that Yamato suffered similar charges.

## Description

The suspected issue is an exposed Google Maps / Google Cloud API key in a Yamato asset. If the key is unrestricted or insufficiently restricted, an unauthorized third party may be able to reuse it outside the intended application context.

## Technical Details

- Finding type: Google Cloud API key exposure
- Asset owner: Yamato
- Detection method: [STATIC_ANALYSIS_OR_MANUAL_REVIEW_PLACEHOLDER]
- Validation method: Safe simulation only; no live Google API abuse performed
- Key restrictions observed: [UNKNOWN_OR_OWNER_VALIDATED_DETAILS]

## Issue #1: Secret Detected, Google Cloud API Key

### Affected File / Asset

```text
[YAMATO_AFFECTED_ASSET_URL_OR_FILE_PATH]
```

### Detected Secret, redacted

```text
[REDACTED_GOOGLE_API_KEY_PLACEHOLDER]
```

## Impact

Potential impact includes:

- Unauthorized third-party use of Maps, Places, or other enabled Google Cloud APIs.
- Unexpected billing or quota exhaustion.
- Reconnaissance through location, geocoding, places, or related metadata endpoints if enabled.
- Availability impact if legitimate application quota is consumed.
- Reputational, legal, and operational impact from exposed credentials.

Actual impact should be determined by Yamato through Cloud Console review of API restrictions, application restrictions, quotas, budgets, logs, and billing anomalies.

## Proof of Concept, safe simulation

The attached `index.html` is a static, Bootstrap-based PoC page. It demonstrates expected risk through local counters, a static map placeholder, and a printable summary section.

Safety properties:

- No real API key is included.
- No Google API script is loaded.
- No Google Maps, Places, or Cloud request is sent.
- No quota-consuming validation is performed.
- All sensitive values are redacted placeholders.

Steps:

1. Open `yamato/google-api-key-poc/index.html` in a browser.
2. Select `Start Simulation` to update local request and cost counters.
3. Select `Render Map Placeholder` to display a static map-like panel.
4. Select `Generate Report Snapshot` to create a printable summary.

## Recommendation

1. Revoke and rotate the exposed key after confirming dependent services.
2. Apply application restrictions appropriate to the client type.
3. Apply API restrictions so the key can call only required APIs.
4. Configure quotas, budgets, and anomaly alerts.
5. Move non-public secrets to a managed secret store.
6. Review repository history, CI logs, build artifacts, and mobile packages for related exposures.
7. Monitor usage logs for unauthorized activity before and after rotation.

## References

- Google Cloud API key best practices: [insert reference link]
- Google Maps Platform API security best practices: [insert reference link]
- OWASP Secrets Management: [insert reference link]
- OWASP Mobile Top 10, insecure communication / secrets exposure: [insert reference link]
- CWE-798: Use of Hard-coded Credentials
- CWE-522: Insufficiently Protected Credentials

## Disclosure Timeline

- [YYYY-MM-DD] Finding identified.
- [YYYY-MM-DD] Report submitted to Yamato through authorized channel.
- [YYYY-MM-DD] Yamato acknowledged report.
- [YYYY-MM-DD] Remediation confirmed.

## Researcher Notes

- Researcher: [RESEARCHER_HANDLE_OR_NAME]
- Contact: [DISCLOSURE_CONTACT_PLACEHOLDER]
- Scope notes: [PROGRAM_SCOPE_NOTES]
- Evidence package: [EVIDENCE_PACKAGE_REFERENCE]
