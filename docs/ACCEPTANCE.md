# Acceptance and release evidence

This is a test specification, not a test report. Every test is **NOT RUN**. Do not mark pass without a reproducible command or browser trace.

| ID | Required behavior | Pass evidence |
|---|---|---|
| AC-01 | Each of three HTTPS origins publishes a conforming public agent network JSON, runtime and usable interface | Public artifact fetch, pinned upstream validator result |
| AC-02 | Agent network actually executes in browser | Clean-browser run and observable tool trace |
| AC-03 | Denying peer access stops loading/calling the peer | Deny test, no unauthorized network/action event |
| AC-04 | Two independently owned peer reads populate comparison | Actual returned payloads, origins, changed fixture proof |
| AC-05 | UI adapts for missing preference, comparison, review, receipt, denial and error | Browser tests and screenshots of real state changes |
| AC-06 | Selecting a slot only creates proposal; cancel changes no booking state | Peer state before/after cancellation |
| AC-07 | Confirm once commits exactly one synthetic booking at selected peer | Peer-origin confirmation and authoritative receipt |
| AC-08 | Replay, forged confirmation, wrong origin, stale slot, expiry fail safely | Adversarial E2E cases and state assertions |
| AC-09 | Invalid, oversized or malicious peer content cannot trigger arbitrary UI or writes | Schema rejection and injection tests |
| AC-10 | Peer timeout, provider failure and partial results remain truthful | Error tests, no fabricated slots or success |
| AC-11 | Keyboard, focus, responsive layout and status messages usable | Desktop/mobile accessibility smoke test |
| AC-12 | No real data, credentials, unapproved spending or private systems | Fixture inspection, redacted logs, secret review |
| AC-13 | Reset clears intended synthetic session state | State reset evidence and documented persistence |
| AC-14 | Required submission artifacts and public URLs work | Fresh browser and Devpost checklist |

## Optional protocol tests

- A2UI: a real compatible renderer receives actual valid messages; unsupported component/malformed message rejected; valid user event dispatches bounded intent; native fallback still works.
- WebMCP: supported browser feature-detection, actual read-only tool registration/invocation, unsupported browser fallback, no booking capability.
- AG-UI: actual compatible event stream and state sync; event replay/invalid event cannot authorize a write.

## Release gate

G0: upstream reproduction → G1: real interoperability → G2: P0 complete → G3: adversarial verification → G4: clean-browser submission proof. No optional integration may excuse a failing required test.

For each test record: date, environment, exact pinned versions, expected result, actual result, evidence link, pass/fail/blocked. Public traces must be sanitized. Keep failures visible.
