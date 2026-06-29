# Sentinel Journal

## 2026-06-16 - Security workflows running on wrong default branch
**Vulnerability:** CodeQL and Secret Scanning workflows were configured to run on the `master` branch, while the repository's active default branch is `main`. This left the default branch un-scanned by these tools.
**Learning:** Hardcoded legacy branch names in GitHub Actions workflows can lead to a silent loss of automated security scanning coverage when the repository default branch is updated.
**Prevention:** Use `main` as the default branch in templates, periodically audit workflow triggers, or consider using wildcards or default branch variables where supported to avoid missing automated security checks.

## 2024-07-01 - Enforcing least privilege in GitHub Actions
**Vulnerability:** The secret-scanning workflow lacked an explicit permissions block, relying on the default GITHUB_TOKEN which can be over-permissioned.
**Learning:** Default tokens in GitHub Actions can grant broader access than necessary, increasing the impact if a workflow is compromised.
**Prevention:** Always explicitly define least-privilege `permissions` at the job or workflow level (e.g., `contents: read`).
