# AEGIS Roadmap

This roadmap is directional. Dates and delivery estimates are not commitments. Public-warning integrations depend on external authorization, partner availability, validation, and applicable law.

## Phase 0 — Repository and requirements
**Goal:** Establish a controlled project baseline.

- [ ] Confirm project name, ownership, and proprietary rights holder
- [ ] Confirm repository visibility and access policy
- [ ] Define threat model and misuse boundaries
- [ ] Write initial architecture decision records
- [ ] Define test-only operating mode and warning lifecycle
- [ ] Create synthetic CAP fixtures and acceptance tests

**Exit criteria:** Scope, non-goals, ownership, and safety rules are documented.

## Phase 1 — MVP foundation
**Goal:** End-to-end warning lifecycle in a test environment.

- [ ] FastAPI application and configuration validation
- [ ] PostgreSQL/PostGIS schema and migrations
- [ ] Alert CRUD and immutable version model
- [ ] Geographic areas and geometry validation
- [ ] User roles and two-person approval workflow
- [ ] Audit events
- [ ] Transactional outbox and simulated dispatcher
- [ ] Test-only dashboard and warning preview
- [ ] Integration tests for publish, update, cancel, and expire

**Exit criteria:** All lifecycle tests pass; no production dispatch adapter is enabled.

## Phase 2 — Interoperability and public information
**Goal:** Standards-based data exchange and safe read-only delivery.

- [ ] CAP 1.2 import/export with schema validation
- [ ] Public read-only warning page for test content
- [ ] Server-Sent Events or equivalent live updates
- [ ] Multi-language content model
- [ ] Accessibility review
- [ ] API rate limiting and abuse protection
- [ ] Delivery metrics and operational dashboards

**Exit criteria:** CAP fixtures validate; public content is clearly marked as test data.

## Phase 3 — Resilience and verification
**Goal:** Demonstrate recoverability and predictable behavior under failure.

- [ ] Backup and restore drills
- [ ] Worker crash and retry tests
- [ ] Idempotency and duplicate-delivery tests
- [ ] Database failover design
- [ ] Load and soak testing
- [ ] Security review and penetration test
- [ ] Incident response and key-rotation runbooks
- [ ] Independent review of audit integrity

**Exit criteria:** Recovery objectives are measured and documented; critical findings are resolved.

## Phase 4 — Controlled pilot preparation
**Goal:** Prepare a non-operational pilot with qualified partners.

- [ ] Identify public-sector, research, and warning-multiplexer stakeholders
- [ ] Document data protection and legal requirements
- [ ] Define integration contracts and authorization boundaries
- [ ] Run tabletop exercises with synthetic incidents
- [ ] Complete accessibility and human-factors testing
- [ ] Define service ownership, support, and escalation model

**Exit criteria:** Written partner authorization and pilot safety case exist before any operational integration.

## Phase 5 — Authorized integrations
**Goal:** Integrate only channels for which explicit permission and technical access exist.

- [ ] Implement isolated adapter per authorized channel
- [ ] Contract tests against partner test environments
- [ ] End-to-end drills with explicit test markers
- [ ] Independent security and operational approval
- [ ] Document channel-specific delivery guarantees and limitations

**Exit criteria:** Each adapter is separately approved; no adapter implies universal reach.

## Long-term — National-scale readiness
- Multi-region operation and tested disaster recovery
- Independent security governance and recurring audits
- Formal service-level objectives and incident management
- Sustainable funding and staffed 24/7 operations if required
- Accessibility, privacy, and legal compliance reviews
- Formal authorization for every official warning channel

## Not on the MVP roadmap

- Direct transmission of Cell Broadcast messages
- Unauthorised access to MoWaS or operator networks
- Claims of guaranteed delivery to all devices
- Autonomous publication of high-severity real-world alerts
- Replacement of official public warning authorities
