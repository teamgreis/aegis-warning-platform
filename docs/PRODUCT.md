# Product Definition

## Mission
Make emergency information easier to collect, assess, authorize, distribute through approved channels, and audit—without hiding uncertainty or overstating delivery.

## Intended users
Authorized operators, local communities, responders, infrastructure operators, NGOs, public authorities, and partner organizations. Permissions and views vary by role; not every user can create or authorize an alert.

## Core workflows
1. Receive an incident report with source, time, location, and provenance.
2. Validate and assess evidence; record uncertainty and conflicting reports.
3. Draft guidance with a defined geographic and temporal scope.
4. Review content and policy requirements.
5. Obtain authorization from an appropriately privileged operator or approved procedure.
6. Dispatch through simulated or individually approved channels.
7. Track dispatch attempts, gateway acknowledgements, and confirmed reception separately.
8. Update, expire, cancel, and review the incident with an auditable timeline.

## MVP scope
- Server-side application and browser-based operator console.
- Incident and source records using synthetic data.
- Role-based access control and auditable state transitions.
- Geographic and time scope for draft guidance.
- Explicit uncertainty and source provenance.
- Simulated dispatch adapters.
- Searchable audit timeline, basic operational health, and export for testing.
- Accessibility and multilingual-ready design.

## Non-goals for MVP
- Issuing real public alerts.
- Replacing government or emergency-service authority.
- Military command or weapons control.
- Guaranteed global reach or guaranteed reception.
- Autonomous AI decisions that trigger real-world action.
- Collecting broad personal data “just in case.”
- Custom hardware or native mobile/desktop apps.

## Product safety requirements
Every alert-like object must identify its status, source, scope, timestamps, authorization, and confidence/uncertainty. Test messages must be unmistakably labeled. Official alerts and AEGIS advisories must not be visually conflated. External formats do not bypass authorization.

## Measures
Evaluate time to assess and authorize, traceability, false-alert resistance, usability under stress, accessibility, recovery time, behavior during network partitions, and accurate reporting of delivery state.
