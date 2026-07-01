# Sentinel Journal

## 2026-06-16 - Security workflows running on wrong default branch
**Vulnerability:** CodeQL and Secret Scanning workflows were configured to run on the `master` branch, while the repository's active default branch is `main`. This left the default branch un-scanned by these tools.
**Learning:** Hardcoded legacy branch names in GitHub Actions workflows can lead to a silent loss of automated security scanning coverage when the repository default branch is updated.
**Prevention:** Use `main` as the default branch in templates, periodically audit workflow triggers, or consider using wildcards or default branch variables where supported to avoid missing automated security checks.
## 2024-07-01 - Workflow Permissons Over-Permissioning Risk
**Vulnerability:** Default `GITHUB_TOKEN` in GitHub Actions runs without explicit `permissions` definitions grants broad privileges by default.
**Learning:** Even simple CI tasks like running `gitleaks` could inherit more access than necessary if the environment is compromised.
**Prevention:** Always define explicit, least-privilege `permissions` at the workflow or job level (e.g., `permissions: contents: read`) to restrict the scope of the default `GITHUB_TOKEN`.
