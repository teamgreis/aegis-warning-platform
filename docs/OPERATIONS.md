# Operations and Recovery

## Environments
- **Development:** synthetic data only; all dispatch sinks simulated.
- **Test/staging:** isolated credentials, test endpoints, visible test banners, and monitored exercises.
- **Production:** not approved for the current prototype. Any future environment requires documented legal authority, partner approval, risk review, and a release gate.

## Release checklist
- Review code and configuration changes.
- Run unit, integration, authorization, and failure-mode tests.
- Verify simulation mode is enabled and no live credentials/endpoints are present.
- Review dependencies, secrets, privacy impact, and audit behavior.
- Test backup and restore.
- Confirm rollback/disable procedures and an accountable operator.
- Document limitations and known risks.

## Dispatch safety
Dispatch is a privileged action. Use explicit role checks, approval policies, idempotency keys, bounded retries, rate limits, and an audit event for every state transition. A failed or uncertain send must not be represented as successful receipt. Duplicate delivery and stale messages must be handled safely.

## Monitoring
Track application health, queue depth, error rates, adapter failures, authorization denials, key/revocation status, audit write failures, synchronization lag, and backup status. Avoid logging secrets or unnecessary personal information.

## Backup and recovery
- Encrypt backups and restrict access.
- Define recovery point and recovery time objectives before any pilot.
- Perform periodic restore drills and document results.
- Protect audit records and key material separately.
- After a node outage, validate identity and policy state before resuming privileged operations.

## Incident response
Contain affected credentials/nodes, revoke compromised identities, preserve relevant audit evidence, communicate status to responsible operators, restore from verified state, and conduct a post-incident review. Do not automatically resume live dispatch after a suspected compromise.
