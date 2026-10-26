# Contributing to AEGIS

Thanks for your interest. AEGIS is proprietary software; repository access does not automatically grant permission to reuse or redistribute code.

## Before contributing

- Obtain approval from the repository owner.
- Do not add credentials, secrets, personal data, or real incident data.
- Use synthetic fixtures and clearly marked test alerts only.
- Keep changes small and document architectural consequences.
- Add tests for lifecycle, authorization, idempotency, validation, and failure behavior where applicable.

## Development expectations

- Use type hints and input validation.
- Prefer explicit state transitions over implicit status updates.
- Do not bypass approval or audit requirements for convenience.
- Do not add an operational channel adapter without written authorization and a reviewed safety case.
- Record significant decisions in `docs/DECISIONS.md`.
- Update documentation and tests with behavior changes.

## Pull requests

A pull request should include:
- Problem and intended behavior
- Risk and security considerations
- Tests run and results
- Database migration notes, if any
- Operational impact and rollback plan

The repository owner decides whether contributions are accepted and what rights are required for submitted work.
