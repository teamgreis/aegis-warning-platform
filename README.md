# AEGIS
### Advanced Emergency Guidance & Information System

**AEGIS is a proposed, modular emergency-warning platform designed to improve how warning information is authored, validated, geographically targeted, distributed, and audited across multiple delivery channels.**

> **Project status:** Concept / early development scaffold. AEGIS is not an official warning service and must not be used to issue real public emergency alerts.
>
> **Important limitation:** This repository does not provide access to Germany's Cell Broadcast infrastructure or MoWaS. Operational distribution through those systems requires authorized integrations, agreements, and the applicable technical and regulatory approvals.

## Vision

AEGIS aims to complement existing public warning infrastructure—not casually replace it—with a shared warning lifecycle, interoperable data formats, secure authorization, geospatial targeting, delivery observability, and channel adapters.

The long-term objective is an independently auditable, resilient platform that can integrate authorized warning channels while making no unsupported promise that any channel can reach every person or device.

## Planned capabilities

- Structured warning creation, review, approval, publication, update, cancellation, and expiry
- Geospatial warning areas and map-based preview
- CAP 1.2 import/export adapter
- Role-based access control and multi-person approval
- Versioned warning records and tamper-evident audit events
- Durable dispatch queue, retries, idempotency, and delivery status tracking
- Public warning portal and optional app / push adapters
- Simulation mode, test alerts, load tests, recovery drills, and observability
- Future authorized integrations with official warning infrastructure and additional channels

## Current scope

This repository starts with architecture and product documentation. The MVP is planned as a **modular monolith with background workers**, not as a premature microservice fleet.

### Proposed stack

| Area | Initial choice |
|---|---|
| API | Python, FastAPI, Pydantic |
| Database | PostgreSQL + PostGIS |
| Durable dispatch | PostgreSQL transactional outbox; worker process |
| Cache / ephemeral coordination | Redis only where useful; never the sole store for critical warning state |
| Web console | React + TypeScript |
| Maps | MapLibre GL JS |
| Authentication | OIDC, MFA, RBAC |
| Interoperability | OASIS Common Alerting Protocol (CAP) 1.2 |
| Packaging | Docker Compose for development; hardened deployment later |
| Testing | pytest, API integration tests, geospatial edge cases, load and recovery tests |

Technology choices are provisional and may change through documented Architecture Decision Records (ADRs).

## MVP acceptance criteria

1. A user with the appropriate role can create a **test-only** warning with validated content and a defined geographic area.
2. A separate authorized reviewer must approve publication.
3. Published versions are immutable references; updates create new versions.
4. The system records actor, action, timestamp, decision, and dispatch outcome.
5. A durable dispatcher can retry failed test-channel jobs without duplicating the logical alert.
6. CAP 1.2 import/export is validated with fixtures and malformed-input tests.
7. Cancellation, update, and expiry are tested end to end.
8. Real public distribution is disabled by default and cannot be enabled merely by a UI toggle.

## Roadmap

See [`ROADMAP.md`](ROADMAP.md) for phases, deliverables, dependencies, and exit criteria.

## Architecture and governance

- [`docs/ARCHITECTURE.md`](docs/ARCHITECTURE.md) — system components and data flow
- [`docs/SECURITY.md`](docs/SECURITY.md) — threat model and security baseline
- [`docs/OPERATIONS.md`](docs/OPERATIONS.md) — deployment and recovery principles
- [`docs/PRODUCT.md`](docs/PRODUCT.md) — scope, users, non-goals, and success measures
- [`docs/DECISIONS.md`](docs/DECISIONS.md) — initial architecture decisions
- [`CONTRIBUTING.md`](CONTRIBUTING.md) — contribution workflow
- [`LICENSE`](LICENSE) — proprietary, all rights reserved

## Safety and responsible use

AEGIS is not a substitute for official emergency services, official warning applications, or instructions issued by competent authorities. Use only synthetic data and clearly marked test alerts during development and demonstrations. Do not send simulated alerts to the public or impersonate official agencies.

Before any operational use, the project requires qualified security review, privacy and legal review, documented operational responsibility, disaster-recovery exercises, accessibility testing, and authorized agreements for every integrated distribution channel.

## License

Copyright (c) 2026 AEGIS Project. All rights reserved.

This repository is proprietary. No permission is granted to use, copy, modify, distribute, sublicense, or create derivative works except where the copyright holder expressly authorizes it in writing. See [`LICENSE`](LICENSE).

**Note:** Replace the copyright-holder placeholder with the actual legal rights holder before publishing. This notice is a starting template, not legal advice.
