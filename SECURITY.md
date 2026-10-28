# Security Policy

AEGIS is intended for a safety-sensitive domain but is not currently an operational emergency-warning service. The prototype must use synthetic data and simulated dispatch only.

## Reporting a vulnerability
Do not publish exploitable details in a public issue. Contact the repository owner privately through an available GitHub security reporting channel. Include the affected component, impact, reproduction steps, and suggested mitigation where safe. Do not include real personal data or live emergency credentials.

## Scope priorities
- Authentication, authorization, and role separation.
- Node identity, key lifecycle, trust revocation, and synchronization.
- Alert approval, dispatch boundaries, replay/deduplication, and audit integrity.
- Privacy, data retention, secrets management, and dependency security.
- Failure recovery, denial-of-service resilience, and safe degraded modes.

## Response expectations
The project will triage reports as capacity permits. Do not assume a fixed response time or that a report has been accepted until acknowledged. Coordinate disclosure so users are not exposed to unnecessary risk.

## Safe harbor
Only test systems and data you own or are explicitly authorized to test. Do not access, disrupt, or transmit to real public-warning infrastructure. Stop testing and report findings if you encounter sensitive data or an unexpected live system.
