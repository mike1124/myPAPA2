# Sentinel Journal

## 2026-06-16 - Security workflows running on wrong default branch
**Vulnerability:** CodeQL and Secret Scanning workflows were configured to run on the `master` branch, while the repository's active default branch is `main`. This left the default branch un-scanned by these tools.
**Learning:** Hardcoded legacy branch names in GitHub Actions workflows can lead to a silent loss of automated security scanning coverage when the repository default branch is updated.
**Prevention:** Use `main` as the default branch in templates, periodically audit workflow triggers, or consider using wildcards or default branch variables where supported to avoid missing automated security checks.

## 2026-06-25 - Missing explicit least-privilege permissions in GitHub Actions
**Vulnerability:** The `secret-scanning.yml` workflow lacked an explicit `permissions` block, leading to default GITHUB_TOKEN over-permissioning.
**Learning:** GitHub Actions workflows without explicit permissions inherit default permissions which may be broader than necessary, violating the principle of least privilege.
**Prevention:** Always explicitly define `permissions` at the workflow or job level (e.g., `contents: read`) to minimize the potential impact of compromised workflows.
