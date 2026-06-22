# Sentinel Journal

## 2026-06-16 - Security workflows running on wrong default branch
**Vulnerability:** CodeQL and Secret Scanning workflows were configured to run on the `master` branch, while the repository's active default branch is `main`. This left the default branch un-scanned by these tools.
**Learning:** Hardcoded legacy branch names in GitHub Actions workflows can lead to a silent loss of automated security scanning coverage when the repository default branch is updated.
**Prevention:** Use `main` as the default branch in templates, periodically audit workflow triggers, or consider using wildcards or default branch variables where supported to avoid missing automated security checks.

## 2026-06-22 - Explicit permissions in GitHub Actions
**Vulnerability:** Workflows lacked explicit permissions, falling back to potentially over-permissive GITHUB_TOKEN defaults.
**Learning:** GitHub Actions defaults can grant write access when only read access is needed.
**Prevention:** Always declare explicit, least-privilege 'permissions:' blocks at the workflow or job level.
