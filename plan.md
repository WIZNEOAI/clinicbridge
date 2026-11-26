# ClinicBridge — execution plan

Status: **planning baseline published; zero implementation tasks complete**.

Target: internal January 4, 2027; official January 11 at 16:00 UTC. Dates below are Mexico City. Planned founder review budget: 24 hours; proposed cash ceiling $25 USD, no unapproved purchases.

| Gate | Window | Founder hours | Exit criteria | Status |
|---|---|---:|---|---|
| G0 | Nov 26–Dec 2 | 4 | Confirm registration and license; pin upstream; reproduce multi-origin example; bounded A2UI spike | Not started |
| G1 | Dec 3–9 | 5 | Hub + two peer sites; real browser peer reads; changed fixture proof | Not started |
| G2 | Dec 10–16 | 5 | Adaptive UI; denial, explicit peer authorization, one simulated commit and receipt | Not started |
| G3 | Dec 17–23 | 4 | E2E, adversarial tests, docs; optional A2UI then read-only WebMCP only if P0 is safe | Not started |
| G4 | Dec 24–Jan 4 | 4 | Freeze, public demo, human narration, screenshots, entrant submission receipt | Not started |
| G5 | Jan 5–10 | 2 | Bug fixes and public availability checks only | Not started |

## Work queue

| ID | Priority | Task | Depends on | Evidence |
|---|---|---|---|---|
| CB-00 | P0 | Entrant registration and official rule/license review | — | Private confirmation, public non-sensitive status |
| CB-01 | P0 | Inspect and pin official spec/runtime | CB-00 | SHA, actual API and license record |
| CB-02 | P0 | Reproduce upstream multi-origin example | CB-01 | Logs, browser proof of approved read and write |
| CB-03 | P0 | Define synthetic fixtures, domain contracts and three origins | CB-02 | Contract docs and fixture ownership tests |
| CB-04 | P0 | Implement actual hub and peer networks | CB-03 | Published JSON/runtime per origin; actual peer reads |
| CB-05 | P0 | Implement adaptive views and partial failure handling | CB-04 | Browser evidence, accessible interaction |
| CB-06 | P0 | Implement origin-bound review/cancel/confirm/receipt | CB-04 | Deny, replay and receipt tests |
| CB-07 | P0 | Complete conformance and adversarial/E2E tests | CB-05, CB-06 | docs/ACCEPTANCE.md and trace artifacts |
| CB-08 | P1a | A2UI real renderer feasibility spike (90 min max) | CB-02 | Supported version, message render and action event |
| CB-09 | P1a | Integrate bounded A2UI catalog if CB-07 passes | CB-07, CB-08 | Genuine wire proof, fallback |
| CB-10 | P1b | Read-only WebMCP capability adapter | CB-07 | Supported browser registration/invocation and fallback |
| CB-11 | P2 | Optional AG-UI event adapter | CB-07 | Official SDK/event trace, no control escalation |
| CB-12 | P0 | Publish three public origins, no secrets, clean-browser smoke test | CB-07 | URLs and actual verification |
| CB-13 | P0 | Record demo and screenshots, English submission text | CB-12 | Real footage, founder narration, public YouTube URL |
| CB-14 | P0 | Entrant approves and submits | CB-13 | Devpost submission confirmation |
| CB-15 | Follow-up | Educational derivatives and retrospective | CB-14 | Content links and lessons |

All tasks remain unchecked. The optional integrations never block P0. A2UI spike can run after CB-02 but cannot displace CB-04–07.

## First session acceptance

Do not spend the first session on visual polish or a new backend. Exit with a pinned upstream SHA, repeatable commands, browser evidence and an explicit go/no-go decision on A2UI. If upstream cannot be reproduced, stop and diagnose before adding protocols.

## Evidence ledger

| Date | Task | Result | Evidence | Next action |
|---|---|---|---|---|
| 2026-11-25 | Documentation setup | Planning baseline only | Repository documents | Confirm entrant registration and start G0 |

Future evidence must distinguish proposed, attempted, verified, blocked and deferred. Maintain links to commits and redacted logs, not private account identifiers.
