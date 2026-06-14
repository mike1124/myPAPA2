# Sentinel Journal

## 2026-06-14 - Disconnected Security Workflows
**Vulnerability:** CodeQL SAST and Gitleaks secret scanning GitHub Actions workflows were configured to run on `master` branch instead of the actual default branch `main`.
**Learning:** Even if security tools are installed and configured, branch naming mismatches can silently disable them. The bandit workflow correctly targeted `main`, but others didn't, resulting in an incomplete security posture.
**Prevention:** Always verify that security workflows target the active default branch, especially when initializing repositories or adapting templates. Ensure uniform branch targeting across all CI/CD pipelines.
