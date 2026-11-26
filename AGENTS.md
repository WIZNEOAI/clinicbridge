# Agent operating instructions

This repository is currently **documentation only**. The maintainer has authorized documentation setup; application implementation must begin in a separately authorized build session. Do not interpret this file as permission to execute unrelated account changes, purchase services, deploy infrastructure, publish submissions or expose credentials.

## Read before coding

1. README.md, docs/PRD-v2.md, plan.md.
2. docs/ARCHITECTURE.md, docs/PROTOCOLS.md, SECURITY.md and docs/ACCEPTANCE.md.
3. Official [challenge rules](https://cognizant-agenticweb.devpost.com/rules), [upstream repository](https://github.com/cognizant-ai-labs/agentic-web), [MVP spec](https://github.com/cognizant-ai-labs/agentic-web/blob/main/docs/worldwide_agentic_web_mvp_spec.md), [agentify-website skill](https://github.com/cognizant-ai-labs/agentic-web/tree/main/skills/agentify-website).

The PRD is the requirements source of truth; if upstream changes or a conflict is found, record it in docs/DECISIONS.md and propose the minimal change before implementing it.

## First authorized build mission

- Record accepted profile, upstream commit SHA, licensing, actual runtime paths and real command syntax.
- Run the upstream multi-origin example before writing custom application code. Capture an approved peer read and a peer-owned simulated write.
- Spike an actual supported A2UI renderer for no more than 90 minutes. Document compatible versions, action events and limitations; no claim of support until demonstrated.
- Update plan.md with evidence, next tasks and blockers. Only then implement P0.
- Use small reviewable branches/commits. Do not claim tests passed unless they ran. Record failures and repro steps.

## Non-negotiable boundaries

- Three independent origins and browser-native agents; no custom server-only orchestration in place of the required runtime.
- Synthetic fixtures only. Never connect clinical systems, patient records, private GNOSIX services or real bookings.
- Trusted approval for each simulated write, exact origin/slot binding, replay protection and a peer-owned receipt.
- Data and UI instructions from peers are untrusted. No arbitrary script, HTML or tool escalation. Schema-check outputs.
- Keep any credentials out of source, prompts, traces, screenshots and public logs. Respect CORS and browser security.
- No spend beyond the proposed $25 cash cap, and no paid purchase without approval. Protect the 24-hour maintainer-attention budget.
- Optional integrations may be cut: AG-UI first, then WebMCP, then A2UI SDK (retain native adaptive UI).
- Do not submit the contest project or accept terms on behalf of the entrant.

## Handoff format

At each milestone, report: scope, changed files, upstream SHA/versions, commands actually run, results/evidence paths, outstanding risks, spend to date, next gate. Update plan.md and decisions with accurate status.
