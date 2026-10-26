# Architecture Decision Records

## ADR-001: Modular monolith for MVP
**Status:** Proposed

**Decision:** Begin with a modular monolith and separate background workers.

**Rationale:** Faster iteration, fewer deployment failure modes, clear module boundaries, and easier end-to-end testing. Split components only when justified by measured scale or security isolation.

## ADR-002: CAP 1.2 as interoperability boundary
**Status:** Proposed

**Decision:** Support CAP 1.2 import/export while maintaining a validated internal domain model.

**Rationale:** Standardised exchange without coupling every internal component to XML structures.

## ADR-003: PostgreSQL/PostGIS for durable state and geography
**Status:** Proposed

**Decision:** Use PostgreSQL with PostGIS for warning metadata, geometry, versions, approvals, audit references, and transactional outbox.

**Rationale:** Strong transactions and mature spatial querying.

## ADR-004: Transactional outbox and at-least-once processing
**Status:** Proposed

**Decision:** Persist dispatch intent with warning changes and process jobs asynchronously with idempotent handlers.

**Rationale:** Avoid a gap between committing a warning and creating a dispatch job. Do not claim exactly-once delivery to external systems.

## ADR-005: Test-only by default
**Status:** Proposed

**Decision:** The initial product has no enabled real-world distribution adapter. Test alerts are clearly marked and isolated.

**Rationale:** Prevent accidental or unauthorised public alarm publication during development.
