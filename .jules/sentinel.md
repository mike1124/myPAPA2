# Sentinel Journal
## 2024-06-13 - Security Tooling Misconfiguration
**Vulnerability:** GitHub Action security workflows (CodeQL, Gitleaks) were targeting the legacy `master` branch instead of the active `main` branch.
**Learning:** Hardcoded branch names in workflows can lead to security tooling silently failing to run on default branches if branch renaming occurs without updating corresponding files.
**Prevention:** Regularly verify that CI/CD triggers match the repository's active default branch. Avoid hardcoding branch names where dynamic configuration is possible, though explicit declaration is common in GitHub Actions.
