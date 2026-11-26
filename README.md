# ClinicBridge

**The web, connected by agents.**

Consent-first, interoperable browser agents with adaptive interfaces.

**WIZNEO Open Agentic Lab · Project 001**

> Status: documentation and planning only. No application, live demo, protocol integration, deployment, or competition submission exists yet.

ClinicBridge is a proposed open-source demonstration for the [Open Agentic Web Challenge](https://cognizant-agenticweb.devpost.com/). A browser agent discovers two independently hosted fictional clinic sites, compares real responses from their synthetic availability data, presents an adaptive interface, and requests explicit human authorization for a simulated booking. The selected peer owns the action and returns an inspectable receipt.

## Why it matters

The aim is to show how independent websites can become agent-operable while remaining human-operable. The project is not a medical assistant or a production scheduling system. It uses exclusively fictional data and performs no real appointments or payments.

## Start here

| Document | Purpose |
|---|---|
| [PRD v2.0](docs/PRD-v2.md) | Authoritative product requirements and constraints |
| [AGENTS.md](AGENTS.md) | Instructions for Claude Code, Codex and other coding agents |
| [plan.md](plan.md) | Ordered work, milestones, owners and evidence |
| [Architecture](docs/ARCHITECTURE.md) | System boundaries and data/action flow |
| [Protocol matrix](docs/PROTOCOLS.md) | Required runtime and gated A2UI, WebMCP, AG-UI extensions |
| [Acceptance tests](docs/ACCEPTANCE.md) | Traceable release and verification checklist |
| [Security](SECURITY.md) | Consent, origin isolation, threat model and reporting |
| [Submission playbook](docs/SUBMISSION.md) | Official deliverables and judging strategy |
| [Content plan](docs/CONTENT.md) | Technical demo and educational derivatives |
| [Contributing](CONTRIBUTING.md) | Development and review workflow |
| [Decisions](docs/DECISIONS.md) | Accepted assumptions and unresolved technical choices |

## Technical direction

- **P0:** Official Open Agentic Web specification and browser runtime; three independent HTTPS origins; native adaptive UI; verified consent and simulated booking.
- **P1a:** A real A2UI integration if the chosen renderer works with the official runtime.
- **P1b:** Experimental read-only WebMCP adapter, with feature detection and a fallback.
- **P2:** AG-UI events only after the required product is stable.
- A2A and production healthcare infrastructure are out of scope.

See the PRD for exact requirements; do not treat proposed versions or integrations as implemented.

## Dates

Internal submission target: **January 4, 2027**. Official deadline: **January 11, 2027, 16:00 UTC** (10:00 Mexico City). Recheck the official competition site before submission. Registration remains pending confirmation by the entrant.

## Project principles

Build once, document reproducibly, share the lessons. Prefer a working standard-conforming product to a long list of protocols. Preserve human authority over actions, and prove each integration with evidence.

**Founder mission:** Build globally competitive AI companies from Mexico.

## License

Apache-2.0 is the proposed project license, pending the maintainer's confirmation and review of the contest and upstream licenses. This planning repository is public, but no license grant has been finalized. Do not copy third-party code into this repository until the license decision is recorded.
