# Safety and security

ClinicBridge is a **fictional administrative scheduling demonstration**, not a medical product. No symptoms, health advice, real appointments, patient data, insurance details, payments or private clinical infrastructure. No claims of healthcare compliance or clinical outcomes.

## Threat model

| Threat | Required control |
|---|---|
| Malicious peer or prompt injection | Treat peer/model output as untrusted data; strict validation and origin allowlist; no implicit tool escalation |
| Unauthorized action | Trusted explicit peer-origin confirmation separate from generated UI; bind exact origin, slot, session and expiry |
| Replay / stale data | Idempotency, expiry and current-slot validation; no duplicate simulated write |
| Cross-origin spoofing | Verify origin, source and message shape; use pinned reference bridge; never bypass CORS or browser sandbox |
| UI injection | Allowlisted components, safe text rendering, bounded event intents; no arbitrary HTML/JS/links |
| Credential exposure | Keep secrets outside repository and public traces; server-side provider key where applicable; redact evidence |
| Resource abuse | Request size/time/rate and model budget limits; safe failure and clear reset |
| Misleading completion | Success only from authoritative peer receipt; label synthetic data and implementation limitations |

No external private system may be connected without separate authorization. Do not add automatic email, messaging, payments or production bookings. Model output cannot approve a write.

## Reporting

Do not post secrets or actual personal information in public issues. Report security concerns privately to the repository maintainer if a private reporting channel is available; otherwise request a private channel through a non-sensitive issue. Include a minimal reproduction using only synthetic data. Do not test against unrelated real services.

Implementation and validation status: **not started**. Security controls above are requirements, not claims of current protection.
