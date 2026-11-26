# Protocol implementation matrix

All statuses below are **not implemented**. Research snapshot: November 25, 2026. Standards and SDKs evolve; verify them in G0.

| Layer | Priority | Intended role | Verification needed |
|---|---|---|---|
| Open Agentic Web MVP | P0 | Browser-native agent networks, public JSON/runtime, inter-site capabilities | Accepted profile and upstream SHA; run official examples and validators |
| Reference nsDeploy runtime | P0 | Execute agent networks and approved peer actions | Actual browser execution and cross-origin trace |
| Native adaptive UI / reference structured UI | P0 | Clarify, compare, review, receipt, error | Actual state-driven surfaces and grounded data |
| A2UI | P1a | Declarative component catalog and bounded dynamic UI | Actual renderer/wire version, validated messages and action event; native fallback |
| WebMCP | P1b | Experimental browser-native read-only site capability exposure | Feature detection, actual supported browser call, no write tool, fallback |
| AG-UI | P2 | Agent/frontend events and state synchronization | Real official SDK/event compatibility, no invented compliance |
| MCP | Conditional | External tools only when genuinely required | Document real endpoint, auth, consent and need |
| A2A | Deferred | Different agent communication protocol | Not in the contest MVP |
| Otari | Optional | Model router/provider access | Eligibility, real inference, key handling, cost and required feedback |

A2UI v1.0 is published but renderer support must be checked; v0.9.1 was the initial stable-renderer candidate in the PRD. Do not silently mix versions. Use the reference runtime UI mechanism first; do not call native UI A2UI/AG-UI.

WebMCP is a browser capability adapter, not a replacement for the official Open Agentic Web network. No automated write, no arbitrary invocation from peer instructions. Browser support is experimental and must not gate the demo.

**Cut order:** AG-UI → WebMCP → A2UI SDK (retain native adaptive UI). Never cut the official runtime, real peer reads, consent or reliable submission.

## Primary references

- [Official challenge](https://cognizant-agenticweb.devpost.com/)
- [Reference repository](https://github.com/cognizant-ai-labs/agentic-web)
- [MVP specification](https://github.com/cognizant-ai-labs/agentic-web/blob/main/docs/worldwide_agentic_web_mvp_spec.md)
- [A2UI](https://a2ui.org/) · [renderer support](https://a2ui.org/renderers/)
- [WebMCP](https://developer.chrome.com/docs/ai/webmcp)
- [AG-UI](https://github.com/ag-ui-protocol/ag-ui)
- [Otari](https://otari.ai/)

Record pinned versions and test evidence before changing any status.
