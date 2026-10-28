# AEGIS Roadmap

This roadmap is directional, not a promise of dates or operational readiness. Each phase has an explicit exit gate. Real public-warning delivery is not part of the early prototype.

## Phase 0 — Foundation and requirements
- Confirm intended users, use cases, and non-goals.
- Define hazard/incident taxonomy, terminology, threat model, privacy requirements, and risk register.
- Define alert lifecycle and separate creation, review, authorization, dispatch, gateway acknowledgement, and confirmed reception.
- Establish synthetic scenario fixtures and acceptance criteria.

**Exit gate:** requirements and safety boundaries reviewed; no real dispatch credentials or endpoints.

## Phase 1 — Test-only software prototype
- Server-side modular monolith with clear module boundaries and background workers.
- Browser-based operator console with accessible, multilingual-ready UI.
- Incident intake, source provenance, confidence/uncertainty, geographic scope, and timeline.
- Role-based access control, cryptographic identity foundations, and append-only audit events.
- Simulated channel adapters; visible simulation labels throughout.

**Exit gate:** automated tests prove unauthorized users cannot approve or dispatch; all external sends remain simulated.

## Phase 2 — Resilience and verification
- Idempotent jobs, retry limits, deduplication, rate limits, and safe degraded modes.
- Signed event envelopes, key rotation/revocation, replay protection, and audit integrity checks.
- Conflict resolution that preserves disagreement and explains uncertainty.
- Backup/restore drills, dependency-failure tests, and incident-response exercises.

**Exit gate:** threat-model review, recovery drill, and independent security review completed.

## Phase 3 — Closed partner pilot
- Only with named, authorized partners and written operating procedures.
- Isolated staging, synthetic or approved test messages, operator training, and monitored exercises.
- Measure usability, false-positive/false-negative risks, accessibility, and recovery time.

**Exit gate:** legal, privacy, safety, and partner approvals documented. No uncontrolled public distribution.

## Phase 4 — Authorized integrations
- Implement adapters to approved existing alerting systems and standards, including CAP where suitable.
- Validate message mapping, signatures, geographic targeting, acknowledgement semantics, and failure behavior.
- Keep official authority-issued alerts visibly distinct from AEGIS-generated advisories.

**Exit gate:** each channel independently approved, tested, monitored, and reversible.

## Phase 5 — Distributed network research
- Prototype independently operated nodes, scoped trust, secure synchronization, and disconnected local operation.
- Test partitions, stale data, conflicting reports, compromised nodes, and safe resynchronization.
- Research radio and other resilient communication gateways with qualified partners.

**Exit gate:** independent review demonstrates bounded authority, no silent privilege escalation, and safe recovery.

## Long-term research
- Specialized AI for decision support, always subordinate to deterministic safety controls.
- Optional sensors, relays, power resilience, receivers, and custom hardware only where justified by validated needs.
- International governance and sustainable multi-stakeholder funding.

## Release gates for every phase
Security review; privacy assessment; accessibility checks; threat-model update; tested backup/restore; documented rollback; operator documentation; and explicit confirmation that the system is not being represented as more operationally capable than it is.
