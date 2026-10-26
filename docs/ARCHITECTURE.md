# Architecture

## Initial shape

Start with a modular monolith plus background workers. Keep module boundaries explicit; split services only when scale, isolation, or operational ownership justifies the added complexity.

```text
Operator / Reviewer
        |
   Web Console
        |
   API Gateway
        |
   Warning Core ---- PostgreSQL + PostGIS
        |                    |
        |              Transactional Outbox
        |                    |
        +-------------- Dispatcher Worker
                              |
                Channel Adapter Interface
                  /       |        \
             Test sink   Web/API   Future authorised adapters
```

## Modules

- **Console:** warning authoring, geographic preview, review queue, status and audit views.
- **Warning Core:** validation, lifecycle, versioning, authorization checks.
- **Geo module:** geometry validation, spatial queries, target-area calculations.
- **CAP adapter:** import/export mapping, schema validation, extension handling.
- **Outbox/dispatcher:** durable jobs, retries, backoff, idempotency keys, dead-letter handling.
- **Channel adapters:** isolated implementation per channel; disabled unless configured and authorized.
- **Audit subsystem:** append-oriented event records and integrity references.
- **Observability:** metrics, structured logs, traces, health checks, and alerting.

## Warning lifecycle

Suggested lifecycle:

`DRAFT -> IN_REVIEW -> APPROVED -> ACTIVE -> EXPIRED`

Additional controlled transitions: `REJECTED`, `CANCELLED`. Updating an active alert creates a new immutable version linked to the same logical alert. Expiry must be enforced server-side.

## Reliability patterns

- Persist warning state and dispatch intent in one database transaction using an outbox.
- Use at-least-once job processing with idempotent handlers; do not claim exactly-once delivery across external channels.
- Retry transient failures with bounded exponential backoff and jitter.
- Separate permanent errors from retryable failures.
- Keep per-channel state and delivery semantics distinct.
- Ensure a dead-letter queue can be inspected and safely replayed.
- Never rely on Redis as the sole durable record of critical warning state.

## Data and standards

- CAP 1.2 as an interoperability boundary.
- PostgreSQL/PostGIS for alert metadata and geographic queries.
- Store source payloads and normalised representations with explicit schema versions.
- Validate all incoming XML securely; disable external entity resolution and protect against oversized or deeply nested documents.
- Use UTC internally and preserve original source timestamps where needed.

## Deployment evolution

1. Local development via Docker Compose.
2. Single-node test deployment with backups and monitoring.
3. Separate staging and production environments.
4. Multi-zone deployment, independent secrets management, and tested disaster recovery only after requirements are defined.

## Scaling principle

Do not promise national scale based on an early prototype. Establish workload assumptions, burst profiles, channel limits, recovery targets, and independent performance tests before capacity commitments.
