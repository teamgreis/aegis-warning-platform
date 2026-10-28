# Architecture Decision Records

Decision status may be Proposed, Accepted, Superseded, or Rejected. Revisit decisions when evidence or constraints change.

## ADR-001: Modular monolith for MVP
**Status:** Accepted  
Start with one deployable application and background workers. Keep module boundaries explicit; split services only when scale, isolation, or operational evidence justifies it. This reduces early operational complexity.

## ADR-002: Server-side prototype
**Status:** Accepted  
The initial product is server-side software with a browser-based operator console. Native desktop and mobile apps are not MVP requirements.

## ADR-003: Simulation-first dispatch
**Status:** Accepted  
All channel adapters default to simulation. Real dispatch stays disabled until legal authorization, partner approval, independent review, and release gates are documented.

## ADR-004: Human and policy authorization
**Status:** Accepted  
AI can provide decision support but cannot bypass deterministic policy, operator permissions, or required human approval. Official alerts and AEGIS-generated advisories must be distinguishable.

## ADR-005: Decentralized, scoped trust
**Status:** Proposed  
Nodes may be independently operated, but network membership alone grants no alert authority. Identity, capabilities, trust, and revocation are explicit and auditable.

## ADR-006: Internal lifecycle plus standards adapters
**Status:** Proposed  
Maintain an internal, auditable lifecycle and use adapters for formats such as CAP. Imported messages must pass local validation and authorization rules.

## ADR-007: Privacy by minimization
**Status:** Accepted  
Collect only necessary information, limit use to stated purposes, define retention, and restrict access. Use synthetic data during development.

## ADR-008: Delivery semantics must be explicit
**Status:** Accepted  
Record message creation, approval, dispatch attempt, gateway acknowledgement, and confirmed reception as separate states. Never equate gateway acknowledgement with human receipt.

## ADR-009: Fail closed for authority-critical actions
**Status:** Accepted  
If identity, policy, authorization, or audit integrity is uncertain, sensitive actions fail closed. Any offline authority must be narrowly pre-authorized, time-bounded, logged, and reconciled.
