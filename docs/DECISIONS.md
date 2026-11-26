# Decision log

These are planning decisions, not implemented facts. Maintain this log as evidence is collected.

| ID | Decision | Status | Rationale |
|---|---|---|---|
| D001 | Official Open Agentic Web runtime is mandatory | Planned | Contest conformance before additional protocols |
| D002 | Hub plus two independent fictional clinic origins | Planned | Demonstrate real peer interoperability |
| D003 | Native adaptive interface as P0 | Planned | Functionality without experimental browser dependencies |
| D004 | A2UI then read-only WebMCP, AG-UI last | Proposed, gated | Real integrations only if P0 remains safe |
| D005 | No real patients, payments, medical advice or private systems | Required | Safety and manageable scope |
| D006 | Three-origin deployment, static-first | Proposed | Minimize overhead and preserve independence |
| D007 | January 4 internal deadline; $25/24h proposed cap | Proposed | Time and cost discipline |
| D008 | Apache-2.0 | Pending | Confirm contest and upstream requirements; maintainer approval |
| D009 | Public documentation repository, no code yet | Completed for documentation setup | Transparent project planning |
| D010 | Entrant registration/team selection | Pending | Requires entrant acceptance of rules and terms |

## Open technical questions

- Which exact upstream SHA and profile are accepted at build time?
- What are actual runtime, peer linking and consent APIs?
- Which A2UI renderer and wire version work with the pinned runtime?
- Which browser/version supports the WebMCP read-only capability test?
- Are model routing and public judging access reliable within the budget?
- Does peer session persistence require a minimal durable endpoint?

## Update template

Date, decision ID, status, alternatives, reasoning, affected requirements, actual evidence, owner approval if needed. Do not change a proposal to verified without execution evidence.
