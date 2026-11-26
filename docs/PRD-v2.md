# ClinicBridge — Product Requirements Document v2.0

**WIZNEO Open Agentic Lab · Project 001**  
**Tagline:** The web, connected by agents.  
**Positioning:** Consent-first, interoperable browser agents with adaptive interfaces.  
**Revision:** 25 November 2026 (Mexico City) · Replaces v1.0 · Approved for planning, registration pending.

## 1. Executive decision

Build a polished, working open-source demonstration of a new interaction model: a visitor asks one browser agent to compare administrative appointment slots across two independently hosted fictional clinic websites. The agent obtains permission to load peer networks, uses their actual shared read capabilities, and adapts the interface to the results. A visitor chooses an option and explicitly approves a simulated booking on the selected clinic's own origin. The booking state is reflected in a receipt and an inspectable action timeline.

The official Open Agentic Web specification is the mandatory interoperability layer. Adaptive UI is a mandatory product outcome, not a requirement to implement every emerging protocol. Use the official runtime's UI and structured-rendering facilities first. A genuine A2UI renderer integration is the preferred first extension; WebMCP is an experimental, read-only browser capability adapter; AG-UI is an optional event adapter. A2A is deferred. These do not replace the official runtime or its security boundaries.

**Target:** finish and submit on 4 January 2027; official deadline 11 January 2027, 16:00 UTC / 10:00 Mexico City. Proposed total cap: 24 founder hours and USD 25 cash spend; do not incur expenses without approval. English product, README and submission; Spanish educational derivative. Work must fit around clinical obligations and sleep.

## 2. Registration and compliance gate

- Register on https://cognizant-agenticweb.devpost.com/ after the entrant expressly accepts the eligibility conditions, official rules and Devpost terms and confirms the team preference. The form previously returned `can_register=true`, `already_registered=false`; do not infer registration from that response. Proposed modality: Working solo.
- Read the full official rules, confirm originality/build-period and AI-assistance restrictions, and recheck deadlines. Do not reuse proprietary GNOSIX code or third-party assets without authorization. Use a public repository for competition materials and preserve license notices.
- Public site must publish a conforming JSON agent network, browser runtime and interaction interface. The entrant must deliver a text explanation, screenshot(s) and public YouTube browser demonstration under two minutes, narrated by the entrant (not AI-generated). Confirm exact fields on the submission form. Optional Otari account email and feedback if used; no secrets in public materials.
- Project is fictional administrative scheduling only. No real patient data, identifiers, medical advice, symptom triage, payments, clinical efficacy claims or real appointments. No production healthcare compliance claim.

## 3. Product thesis and target audience

**Primary user:** a visitor comparing fictional administrative service availability without opening many tabs. **Secondary user:** a developer learning how to make a normal website both human-operable and agent-operable.

**Problem hypothesis:** isolated web interfaces force manual comparisons and opaque automation makes action authority unclear. **Proposed solution:** portable browser-executed peer agent networks, site-owned actions and UI that changes with the task while explicitly separating suggestions from authorization.

**Judging story:** this is not a scheduling chatbot with two hardcoded integrations. It is a demonstrable pattern for turning independently operated websites into composable capabilities. A generic adaptive-interface adapter could apply to travel, education, events and other administrative workflows, without building those domains now.

## 4. Experience design

### 4.1 UI surfaces and observable behavior

| Surface | Trigger | User experience / source of truth |
|---|---|---|
| S0 — Welcome | New session | Fictional-data disclosure; text input, example prompts, known peer origins, model settings and budget status. |
| S1 — Clarify | Missing date/time or administrative constraints | Agent requests only missing information using a date/time input or choice widget; typed, validated values. |
| S2 — Peer permission | Before a peer call | Trusted runtime consent card shows exact origin and what will be shared. Deny or cancel actually stops that call. |
| S3 — Compare | Structured peer results | Render 0, 1 or 2+ options, actual returned prices (fictional), dates, timezone, origin, freshness, partial failures and select buttons. Agent can choose a comparison layout but cannot invent data. |
| S4 — Review | User selects one valid slot | Show immutable proposal summary with selected peer origin, slot, data and expiry; route to the peer's trusted confirmation UI for the simulated commitment. |
| S5 — Receipt | Peer reports confirmed simulated booking | Show verified response/receipt ID, selected slot, outcome and timestamp. Never show success from model text alone. |
| S6 — Error / denied | Missing permissions, invalid data, unavailable peer, limit exceeded | Explain outcome, preserve safe results, allow explicit retry or reset. |

Persistent shell: session state, cancel/reset, model configuration, activity trace and synthetic-data banner. Chat is one affordance, not the entire application. Keyboard operation, focus management, accessible status announcements, responsive English layout. Peer pages must also be independently human-operable; their visible availability and simulated booking state come from the same code used by their actions. WIZNEO visual direction: near-black, restrained green accents, readable neutral text, no decorative third-party logos in competition video without permission.

### 4.2 Canonical demonstration

1. Open ClinicBridge and request “Find a fictional introductory consultation next Friday afternoon.” Resolve relative dates visibly against session time; allow a fixed demo-date preset.
2. Authorize each listed peer before its network is loaded/called. Show the loading/trace state.
3. Two real peer reads return different synthetic slots. The interface transforms into a comparison surface, not an ungrounded chat response.
4. Change a preference (e.g. latest time or lowest fictional price). Update the surface from validated results; requery only when necessary.
5. Select a valid slot. The agent proposes a booking; the selected origin displays trusted confirmation. Cancel once (no booking). Re-select/review and confirm once (one booking).
6. Display the peer receipt and action trace; demonstrate the selected peer's own visible booking state. A reset or explicit session expiry clears synthetic session data.

## 5. Protocol architecture and priorities

### P0 — Mandatory core; always ship first

**Open Agentic Web MVP Profile 0.3** (18 November 2026, upstream page inspected; README says 0.2 and 0.3 are accepted). Confirm latest accepted profile and pin upstream commit before coding. The reference `nsDeploy` browser runtime executes the graph, including peer networks loaded in the caller's browser. Use upstream `skills/agentify-website` and its linked guesthouse/harbor/pizza examples. Do not conflate peer graph loading with an HTTP call to a remotely hosted model agent.

Three independent HTTPS origins: `hub`, `clinic-a`, `clinic-b` (actual URLs TBD). All publish correct manifests and resolved network JSON. The hub references approved peer network URLs; each peer owns its synthetic availability and booking handlers. The reference bridge provides origin-checked peer read/write transport when compatible with the pinned version. Its documented implementation runs permitted reads in a peer frame and opens a peer-origin window for confirmed writes. Exact paths, manifest fields and handler signatures must come from upstream, not guesses. Cross-site action transport is not itself mandated by the minimum profile; this project deliberately demonstrates the reference extension.

Adaptive interface P0: implement a bounded view-state model and use the reference runtime's structured UI, including CRUSE if present in the pinned version, or a small native renderer. Preserve the trusted consent and confirmation layer. A real model selects the view and/or tool, while authoritative validated state provides data and controls. Do not claim native UI or CRUSE is A2UI/AG-UI. No hard dependency on Chrome preview or external UI service.

MCP is the baseline external tool/data interface in the spec. Use the runtime's site actions for this local/peer demo. A separate MCP server is not needed just to add a logo; if introduced, require appropriate third-party consent, authentication and documented compatibility. Do not publish an MCP endpoint claiming capabilities that do not exist.

### P1a — Preferred differentiation: A2UI (actual implementation)

A2UI describes dynamic UI with validated declarative messages and a known component catalog. Use the maintained web renderer and a stable, supported version, initially target **v0.9.1** because the official renderer matrix lists stable web implementations for it while v1.0 support is listed as planned. The published specification is now v1.0; pin compatible SDK and wire version after a <= 90-minute spike. Use v1.0 only if the actual chosen renderer demonstrably supports it. Do not handwave compatibility or mix wire envelopes across versions.

Minimal catalog: standard text, columns/rows, cards, buttons, choice input; no arbitrary HTML, script, external URL/image, or arbitrary function execution. Start with the official basic catalog, styled with our own theme. A local adapter receives a constrained agent intent such as `compare` or `clarify`, selects a valid surface structure, and binds it to authoritative typed results. For richer generative UI, optionally let the agent propose a schema-valid component tree from that limited catalog. Validate it before rendering. Render at least two genuinely distinct surfaces and show a live data update. Keep permission, irreversible confirmation, errors and receipts controlled by trusted application code outside the generated tree. A2UI action events may select a slot or update a filter; they cannot authorize an irreversible operation. Reject unknown components, unsupported wire versions and illegal event IDs, and fall back to native UI.

Acceptance: a real A2UI renderer processes messages conforming to the pinned spec; capture the validated wire messages and a browser trace/screenshot. A user action updates app state and a subsequent valid UI update. If only a local deterministic mapping is used, say “A2UI-rendered adaptive UI,” not unrestricted agent-generated layouts. If time/compatibility fails, cut this extension and ship the working native adaptive interface.

### P1b — WebMCP (experimental, read only)

WebMCP exposes typed page functions to compatible browser agents. It is **not** the Open Agentic Web peer transport. Chrome documentation describes early preview/flag requirements; the upstream runtime FAQ explicitly says WebMCP is not yet supported by its agentify skill and the MVP spec lists it as future work.

Implement a tiny independent adapter only after core and A2UI work: feature-detect the actual browser API in the tested Chromium release (`document.modelContext` or other verified current API surface; do not assume a historical property name), secure context, version and flag as required. Register exactly one read-only tool on a clinic page: `clinic_list_availability`. A second read-only `clinic_get_services` only if trivial. Both use the same typed handler and data as native UI and runtime site actions; do not expose booking, reset, model secrets or arbitrary commands via WebMCP. Unsupported browsers keep the normal UI and the official reference runtime fully functional. No fabricated shim presented as a native WebMCP integration.

Acceptance: screenshot/recording and browser version of a compatible agent/tool inspector actually invoking the registered page capability; output matches the native view. In a normal browser without WebMCP, no exceptions or lost functionality. Document that this is a progressive enhancement, not official runtime support. Timebox <= 2 hours; remove if it jeopardizes delivery.

### P2 — AG-UI (optional event adapter; cut first)

AG-UI standardizes bi-directional agent/frontend events and state. It is not itself a UI renderer, nor a peer discovery protocol. If there is a supported path to observe the pinned browser runtime, map lifecycle, state and tool activity into the official AG-UI event schemas using a small local adapter, without moving agent orchestration to a server or duplicating the policy engine. Start with run start/end/error and snapshot; add tool events or delta only if exposed reliably. Verify exact event types, IDs, ordering and official package version against docs. If using only an internal event bus, label it as such; do not claim AG-UI conformance. No SSE/backend just for protocol optics. Optional proof: actual AG-UI-compatible consumer processes validated events. Defer full protocol claims, A2A, NANDA registry publication and MCP Apps until after submission unless a small official example makes them essentially free.

## 6. Functional requirements and evidence

| ID | Priority | Testable acceptance |
|---|---|---|
| FR01 | P0 | Pin upstream SHA and profile; all public network JSON and runtime artifacts load and validate; archive validation logs. |
| FR02 | P0 | Three independent HTTPS origins, explicit peer allowlists and correct public-file CORS. Peer checks pass; runtime graph calls load the peers' definitions rather than executing fake hub-only tools. |
| FR03 | P0 | A real model-driven browser agent selects a capability and obtains typed availability from both peers. Modify a peer fixture and show output changes without changing the hub. |
| FR04 | P0 | Adaptive clarify, comparison, approval, receipt and error surfaces. No model-invented slots, prices or receipts. Native/manual path remains usable. |
| FR05 | P0 | Peer consent precedes network load/calls; reject unauthorized origins. Irreversible booking executes only after trusted peer-origin approval. Denial and cancellation create zero bookings. |
| FR06 | P0 | Validate typed arguments, slot state, origin, scope, expiry, replay and idempotency; same proposal commits at most once. Session-scoped synthetic ledger or in-memory demo clearly documented. |
| FR07 | P0 | Display observable runtime action trace: origin, capability, phase/status and redacted details. Distinguish action log from cryptographic provenance. |
| FR08 | P0 | Clean-browser judge access via capped publisher-funded inference if affordable, or verified supported visitor-funded/BYOK path. Prefer no-key demo. No credential in network JSON, prompt, peer messages or client bundle; handle exhaustion gracefully. |
| FR09 | P0 | Tests for partial peers, timeouts, invalid output, prompt injection, stale proposals, cancel, mobile/desktop, keyboard and reset. |
| FR10 | P1a | Actual validated A2UI surfaces render and update through a pinned supported SDK; native fallback works. Generated surface cannot bypass authorization. |
| FR11 | P1b | Native WebMCP read-only tool call demonstrably works in compatible browser; no dependency on it for official demo. |
| FR12 | P2 | Official AG-UI-compatible event consumer validates real events, if implemented; otherwise internal events only. |
| FR13 | P1 | Document the reusable capability adapter/typed UI pattern with a minimal example and tests, only after all P0 gates. |

## 7. Data model, action contract and security

Illustrative internal domain types, **not** claimed official wire schemas:

```ts
type Slot = { slotId: string; origin: string; serviceId: string; startISO: string; timezone: string; priceMinor: number; currency: string; observedAtISO: string; synthetic: true };
type BookingProposal = { proposalId: string; origin: string; slotId: string; expiresAtISO: string };
type Receipt = { receiptId: string; origin: string; slotId: string; status: 'confirmed'; confirmedAtISO: string; synthetic: true };
```

Site-owned typed actions: `list_services`, `list_availability`, `prepare_booking`, `confirm_simulated_booking` (irreversible), `cancel_proposal`. Map names/effect classification/transport to pinned runtime API. Use one shared handler per operation, not separate fake WebMCP/agent fixtures. UI intent and runtime action contracts are separate; an agent cannot mutate authoritative availability or the approval status. The proposal ID is opaque and scoped to session, origin and slot. Booking confirmation must be issued by trusted peer-owned code after real user activation; never accept model-generated approval, unchecked UI payload or a caller-supplied boolean as proof of consent. Duplicate calls return the same receipt or reject without additional mutation. For static demo, state persistence and limits must be documented; add a minimal peer-owned durable endpoint only if required for reliable judging within budget. Never claim production-grade transactions from tab-local state.

Other controls: HTTPS, origin allowlists, origin/source validation for any bridge messages, strict schema checks, reasonable size/rate/time limits, deny-by-default private context, sanitize rendered text, no arbitrary executable content from agents, CSP compatible with the pinned runtime/renderer, no untrusted links in dynamic UI, isolate credentials, no secret in logs. Do not bypass browser sandbox/CORS. Booking confirmation UI outside the generated component tree; no model or injected peer instruction can escalate a read to a write. Synthetic fixtures explicitly labeled. Reset must not silently change real systems; none connected.

## 8. Implementation shape

Node.js 22+ per upstream skill, TypeScript, native web or light framework chosen after reference spike; React or Lit only if necessary for the pinned A2UI renderer. Static hosting with three deployments on Vercel or equivalent if suitable; no custom agent backend. Optional narrow model proxy, strict spend/rate controls and key kept server-side; BYOK only through supported runtime model settings. Optional Otari credits if eligible and actually available. No subscription, CRM, Convex, Clerk or database unless proven essential. Keep separate from GNOSIX and existing client work.

```text
clinicbridge/
  apps/hub/                    # runtime, agent network, adaptive UI
  apps/clinic-a/               # independently deployable agentic site
  apps/clinic-b/               # independently deployable agentic site
  packages/domain/             # typed synthetic fixtures and validation
  packages/ui-adapter/         # native; optional real A2UI adapter
  packages/webmcp-adapter/      # P1b only
  packages/event-adapter/       # P2 only
  tests/                       # validation, browser E2E, adversarial tests
  docs/                        # pinned sources, threat model, proof, demo
  README.md
  LICENSE
  plan.md                      # live tasks, gates, evidence, decisions
```

Public paths, generated bundles, bridges and manifest schemas follow upstream. Proposed Apache-2.0 license, subject to official rules and dependency review. Preserve all third-party notices. Record exact pinned versions, build commands, environment requirements and deployment URLs in README. Do not commit credentials.

## 9. Validation plan and release gates

**Gate A — conformance:** run upstream `build_network.mjs --check`, `serve_site.mjs`, `check_partner.mjs` per their actual CLI usage and each site/peer origin. Run the official challenge validator if released before submission; distinguish official conformance tests from skill-specific checks. Capture logs and version/SHA. Check public artifacts and CORS in a clean browser.

**Gate B — end-to-end:** real LLM tool calls from hub to both peer networks, proof of data ownership at peers, UI update, cancel, one approved commit, receipt at selected peer. Record network/trace evidence with secrets redacted. Test changed peer fixture to demonstrate grounding.

**Gate C — adversarial:** deny peer, unlisted origin, forged confirmation, replay, expired/changed slot, malformed response, oversized response, injected instructions, timeout, unavailable peer, provider quota exhaustion and reset. Unknown UI component/event or A2UI malformed message must fail closed. If WebMCP enabled, verify read-only capabilities and fallback. Test mobile and desktop, focus and keyboard. Do not count unrun tests as passes.

**Gate D — optional protocols:** test actual SDK wire formats and browser capabilities as described in section 5. Include compatibility table distinguishing implemented, experimental, deferred and native fallback. Don't claim compliance based solely on conceptual similarity.

**Gate E — submission:** public URL(s) accessible through judging period, working model access, no secrets, public repository and license, screenshot(s), human-narrated public YouTube video under 2 minutes, description and Devpost receipt. Re-read final rules and form.

## 10. Judging strategy and scope discipline

Four official dimensions, scored 1–5: technical implementation, design, potential impact, quality of idea. Prioritize spec fidelity and live proof; visual task-based interaction; credible administrative workflow with clear limitations; a small reusable adapter or tutorial that benefits other builders. Optional standards are differentiators only when demonstrably functional. No prediction or guarantee of prize.

Cut order if time slips: AG-UI → WebMCP → A2UI SDK (retain native adaptive UI) → extra catalog/components → optional provider integrations. Never cut user authorization, two independent peer reads, real browser runtime, basic UI, safety tests or required submission artifacts. If peer action bridge is blocked, resolve with official example first; if unresolved, document limits and use a clearly identified peer-owned approval path rather than simulate cross-origin success. Do not misrepresent partial conformance.

## 11. Roadmap (24 founder hours; dates in Mexico City)

| Window | Hours | Exit gate |
|---|---:|---|
| Nov 26–Dec 2 | 4 | Entrant registers; pin spec/runtime; run upstream multi-origin example; prove browser action; short A2UI feasibility spike. |
| Dec 3–9 | 5 | Three local/deployed origins, validated peer reads and correct CORS, changed fixture proof. |
| Dec 10–16 | 5 | Adaptive native interface, approval/commit/receipt; P0 feature complete. |
| Dec 17–23 | 4 | Security/E2E checks, documentation; A2UI integration if gate permits; then read-only WebMCP if still within cap. |
| Dec 24–Jan 4 | 4 | Release freeze, optional AG-UI only if no risk, clean-browser test, video, screenshots, final submission receipt. |
| Jan 5–10 | 2 | Bug fixes only; confirm all public URLs remain valid. |

Coding agents may draft implementation and tests; founder reviews concrete evidence at milestones. Do not assume unattended execution or guaranteed schedule. If clinical duties conflict, cut P1/P2 rather than sleep or clinical responsibilities. No unapproved spending. Reserve required demo/video time before integrations.

## 12. Demo and content plan

**Official video, target 110 seconds; actual founder voice in English.** 0–12s: problem and synthetic-data disclosure. 12–30s: show three URLs and browser runtime. 30–55s: approve peer access, compare live returned slots, adaptive UI changes. 55–80s: review/cancel then confirm at peer origin. 80–95s: verified receipt and activity trace. 95–110s: public repository and actual verified extension (A2UI/WebMCP if shipped), impact. No AI-generated narration, fake UI footage, unlicensed marks/music or private patient information.

One build, many assets: open-source README and minimal reproduction; official English demo; Spanish WIZNEO long-form tutorial “Building the Agentic Web”; WIZ AI Club Construye lab; three short clips (peer discovery, adaptive UI, consent); simulated GNOSIX technical case study; founder networking discussion. Publish open-source contest material freely; paid educational extras add teaching value rather than lock required source. No claim of actual clinical benefit, investment or prize.

## 13. Coding agent kickoff — do this first

1. Read this PRD and rules, then clone upstream https://github.com/cognizant-ai-labs/agentic-web. Read `docs/worldwide_agentic_web_mvp_spec.md`, `skills/agentify-website/SKILL.md`, the linking guide and multi-origin example READMEs. Pin a concrete SHA and report accepted profile, license and actual scripts/APIs.
2. Run the upstream three-origin example and capture commands, real output and browser action/consent evidence. Prove one approved cross-origin read and one peer-owned simulated write; document failures honestly. Do not start a custom backend or UI protocol before this gate.
3. Spike a stable A2UI renderer (max 90 min), validate one surface and an action event; report version, compatibility and cost. Check official WebMCP docs/API support and AG-UI event schemas without integrating them yet. Mark any unsupported approach deferred.
4. Create a local `plan.md` with ordered P0 tasks, architecture decisions, test commands, trace evidence and hard stop criteria. Begin incremental P0 implementation after the gate. One reproducible commit per milestone. Keep optional work feature-gated. Do not create public accounts, publish a repo, purchase services or submit on behalf of the entrant without authorization. No key in prompts, code, trace or artifacts.

## 14. Sources and version record

Official challenge: https://cognizant-agenticweb.devpost.com/ · https://cognizant-agenticweb.devpost.com/rules · https://info.devpost.com/terms

Open Agentic Web: https://github.com/cognizant-ai-labs/agentic-web · https://github.com/cognizant-ai-labs/agentic-web/blob/main/docs/worldwide_agentic_web_mvp_spec.md · https://github.com/cognizant-ai-labs/agentic-web/tree/main/skills/agentify-website · https://worldwideagenticweb.org/

A2UI: https://a2ui.org/ · https://a2ui.org/renderers/ · https://a2ui.org/concepts/catalogs/ · https://a2ui.org/specification/v1.0/schemas/

AG-UI: https://github.com/ag-ui-protocol/ag-ui · https://github.com/ag-ui-protocol/ag-ui/blob/main/docs/introduction.mdx · https://www.copilotkit.ai/ag-ui-and-a2ui

WebMCP: https://developer.chrome.com/docs/ai/webmcp · https://developer.chrome.com/docs/modern-web-guidance/guides/webmcp/webmcp

Optional inference: https://otari.ai/

Research snapshot: 25 November 2026 CDMX. The official spec is evolving; the exact runtime SHA, SDK versions, APIs, native WebMCP test browser, deployed origins, model access, licensing review and budget are **not yet verified by execution**. This document is a requirements and implementation plan, not a working project or evidence of successful registration. The previous v1 file remains unchanged.