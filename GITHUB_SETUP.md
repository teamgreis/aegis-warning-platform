# GitHub repository setup

## Repository
- Owner: `teamgreis`
- Repository: `aegis-warning-platform`
- Main development branch: `main`

## Access and protection
- Grant the minimum required permissions to collaborators and integrations.
- Prefer short-lived, narrowly scoped credentials and revoke unused integrations.
- Never share passwords, personal access tokens, private keys, recovery codes, or session cookies in issues, chats, or commits.
- Enable branch protection when team workflow supports it: require pull-request review, passing checks, and no force-pushes to the protected branch.
- Review GitHub App access at the account/organization settings and restrict it to the specific repository where possible.

## Suggested repository hygiene
- Keep secrets out of the repository; use environment variables or a secrets manager for local development.
- Add automated formatting, linting, type checks, and tests as implementation is introduced.
- Use issue templates for bugs, feature proposals, security concerns, and architecture decisions.
- Keep release notes and update the roadmap when scope changes.

## Safe development
Early environments must use synthetic data and simulated dispatch sinks. Do not add live emergency endpoints or credentials. Any future production integration needs documented authorization, partner approval, security/privacy review, monitoring, and a tested disable/rollback procedure.

## Pushing changes
Use GitHub's web editor, GitHub Desktop, Git, or an authorized development integration. Review the diff before committing. If an integration returns HTTP 403, check that it is installed for the correct owner/repository and has the required contents write permission; do not work around the restriction by exposing credentials.
