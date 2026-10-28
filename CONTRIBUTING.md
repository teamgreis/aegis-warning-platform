# Contributing to AEGIS

Thanks for your interest. AEGIS is an early-stage, safety-sensitive project. Contributions should improve clarity, reliability, security, accessibility, or testability without overstating operational readiness.

## Before contributing
1. Read the README, roadmap, architecture, product definition, and security baseline.
2. Open an issue or proposal for substantial changes.
3. State the problem, intended users, assumptions, risks, and how the change will be tested.
4. Use synthetic examples only. Never include real personal data, secrets, private keys, or sensitive incident information.

## Safety rules
- All channel adapters must default to simulation.
- No live public alerting, emergency-service integration, or transmission of real warnings without documented authorization and a reviewed release gate.
- AI must not bypass identity checks, policy rules, human approval, or channel authorization.
- Do not conflate message creation, authorization, dispatch, gateway acknowledgement, and human receipt.
- Preserve provenance, uncertainty, disagreement, and audit history.
- Avoid collecting data that is not needed for the stated purpose.

## Pull requests
- Keep changes focused and explain trade-offs.
- Add or update tests, documentation, threat models, and decision records where relevant.
- Include failure-mode tests for retries, duplicate events, stale data, unauthorized access, and partial connectivity when applicable.
- Never commit credentials, production endpoints, or real alert payloads.
- Do not claim compliance, certification, or operational readiness without evidence.

## Review
Security-sensitive changes require additional review. Changes to authorization, trust, dispatch, cryptography, retention, or external integrations should not be merged solely because tests pass.

## License and reuse
The repository currently declares a proprietary license. A contribution does not imply permission for third parties to reuse or redistribute the project. Clarify ownership and permission before contributing code from another source.
