# Product Definition

## Mission

Make emergency-warning information easier to author, validate, target geographically, distribute through authorized channels, and audit—while preserving clear authority boundaries and avoiding dependence on any single delivery mechanism.

## Intended users

- Authorized warning officers and reviewers
- Emergency-management and public-sector partners
- Technical operators and security staff
- Researchers and evaluators in controlled test environments
- Public users consuming published warning information

## Core principles

1. **Safety before reach:** incorrect or unauthorised alerts are a critical failure.
2. **Multi-channel, not magical:** channel diversity improves resilience but cannot guarantee delivery.
3. **Authority is explicit:** the platform does not confer authority to issue official warnings.
4. **Fail closed for publication:** missing approval, invalid signatures, or invalid payloads block publication.
5. **Traceability:** all consequential actions are attributable and reviewable.
6. **Accessible by default:** plain language, localisation, screen-reader support, and usable contrast.
7. **Privacy minimisation:** avoid collecting location or identity data unless required for a documented purpose.
8. **Interoperability:** use documented standards and versioned adapters.
9. **Test isolation:** simulated alerts must never be confused with real public warnings.

## Non-goals for the MVP

- Issuing official public warnings
- Replacing MoWaS, Cell Broadcast, NINA, KATWARN, or competent authorities
- Operating cellular radio infrastructure
- Guaranteeing alert reception or user acknowledgement
- Autonomous AI-generated public warnings
- Collecting continuous user location histories

## Initial success measures

- Correct lifecycle transitions under automated tests
- No publication without required approvals
- No loss of committed alert state during tested worker restarts
- Deterministic handling of duplicate dispatch jobs
- CAP validation against maintained fixtures
- Measured recovery time and recovery point in drills
- Accessibility and security findings tracked to closure
