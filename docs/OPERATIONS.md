# Operations and Recovery

## Environments

- **Development:** synthetic data only; all dispatch sinks simulated.
- **Staging:** isolated credentials and test endpoints; conspicuous test markings.
- **Production (future):** only after formal authorization, operational ownership, independent review, and approved runbooks.

## Minimum telemetry

- API request latency and error rate
- Queue depth and oldest pending job age
- Dispatch attempts and outcomes by channel
- Invalid payload and approval rejection counts
- Database health and connection saturation
- Worker heartbeat and restart count
- Backup freshness and restore-test status
- Signing-key status and key-rotation events

Never log secrets, authentication tokens, unnecessary personal data, or private key material.

## Backup and restore

- Define recovery point objective (RPO) and recovery time objective (RTO) before production.
- Use encrypted backups with access separated from the application runtime.
- Test full restoration on a schedule and after major schema changes.
- Record restore duration, data integrity checks, and unresolved gaps.
- Protect audit data and key metadata independently.

## Failure handling

- Database unavailable: do not acknowledge a write as committed.
- Dispatcher unavailable: retain durable pending jobs; alert operators.
- Channel unavailable: retry within policy, expose stale/pending state, and never report delivery success without confirmation.
- Invalid or revoked signing key: block publication.
- Approval service unavailable: fail closed for publication.
- Clock skew: monitor and reject invalid freshness windows where required.
- Partial channel success: report outcomes per channel, not as a single misleading global success.

## Exercise scenarios

1. Worker termination during dispatch.
2. Duplicate job delivery.
3. Database restart and restore.
4. Expired or revoked signing key.
5. Invalid CAP payload and oversized input.
6. External channel timeout.
7. Loss of one hosting zone.
8. Operator account compromise simulation.
9. Accidental test-alert publication attempt.
