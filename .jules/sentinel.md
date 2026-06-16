# Sentinel Journal

## 2026-06-16 - Security workflows running on wrong default branch
**Vulnerability:** CodeQL and Secret Scanning workflows were configured to run on the `master` branch, while the repository's active default branch is `main`. This left the default branch un-scanned by these tools.
**Learning:** Hardcoded legacy branch names in GitHub Actions workflows can lead to a silent loss of automated security scanning coverage when the repository default branch is updated.
**Prevention:** Use `main` as the default branch in templates, periodically audit workflow triggers, or consider using wildcards or default branch variables where supported to avoid missing automated security checks.
