# Architecture

## Architecture goals
AEGIS should be modular, auditable, resilient to partial failure, and safe by default. The initial design is a modular monolith with background workers—not premature microservices. Modules must have explicit interfaces so components can be separated later when scale, isolation, or operational evidence justifies it.

## Initial logical modules
- **Identity and access:** user authentication, roles, service identities, scoped permissions, revocation.
- **Incident intake:** reports, provenance, timestamps, geospatial scope, evidence references.
- **Assessment:** source reliability, corroboration, uncertainty, conflicts, and confidence history.
- **Alert lifecycle:** draft, review, approval, scheduled, dispatched, acknowledged, expired, cancelled.
- **Policy engine:** deterministic rules for who may do what, where, and under which authorization.
- **Channel adapters:** simulation first; future channels individually authorized and isolated.
- **Audit ledger:** append-oriented events for sensitive actions, approvals, and delivery evidence.
- **Operations:** health, metrics, backup/restore, key rotation, and safe shutdown.

## Trust boundaries
Treat users, nodes, data sources, AI output, external adapters, and imported messages as potentially untrusted. Validate all inputs. Imported formats (including CAP) do not bypass local authorization. Joining a network does not grant alert-issuing privileges.

## Distributed operation
Long-term nodes may be independently operated. Each node has a cryptographic identity, scoped trust level, revocation status, and explicit capabilities. Synchronization must handle partitions, duplicates, replay, stale messages, and conflicting updates. After reconnection, reconciliation must preserve provenance and disagreement rather than silently overwrite it.

## AI boundary
AI may summarize, classify, detect patterns, and suggest next steps. It must disclose uncertainty and evidence. Deterministic policy and authorization remain authoritative; AI cannot issue official alerts, expand its own permissions, or directly enable live dispatch.

## Communication and reach
The architecture may support web interfaces and future gateways to existing alert systems, radio, or other channels. Actual reach depends on powered hardware, physical coverage, spectrum access, service providers, partner agreements, and applicable law. The software must not imply delivery to a person when only a gateway acknowledgement is available.

## Security controls
Least privilege; multi-factor authentication for privileged operators; secure secret storage; key rotation and revocation; signed events where appropriate; rate limits; idempotent dispatch jobs; replay protection; immutable or tamper-evident audit; encryption in transit and at rest; tested backup/restore; dependency scanning; and documented incident response.

## Failure behavior
If identity, authorization, policy, or audit integrity cannot be established, sensitive actions fail closed. Read-only access and clearly marked degraded operation may remain available. No automatic failover may silently broaden authority.
