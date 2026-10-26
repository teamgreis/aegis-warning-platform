# GitHub repository setup

Recommended repository name: `aegis-warning-platform`
Recommended owner: `teamgreis`
Recommended visibility: **Private** while the code and proprietary terms are being finalised.
Description: `A modular, multi-channel emergency-warning platform focused on secure alert lifecycle management, geospatial targeting, interoperability, and resilience.`
Topics: `emergency-alerts`, `public-safety`, `cap`, `fastapi`, `postgis`, `disaster-response`, `security`

## Initial setup using GitHub CLI

Run from the extracted repository directory after installing and authenticating `gh`:

```bash
gh auth status
git init
git add .
git commit -m "chore: initialize AEGIS project foundation"
git branch -M main
gh repo create teamgreis/aegis-warning-platform --private --source=. --remote=origin --push
```

If the repository already exists, create it in GitHub first and use its actual remote URL instead of `gh repo create`.

Before publishing, replace the copyright holder in `LICENSE` and `README.md` with the correct legal owner. Keep the repository private until ownership and the proprietary license text have been reviewed.
