# Sentinel Journal

## 2026-06-15 - Security Scanners Not Running Due To Branch Misconfiguration
**Vulnerability:** Found that critical security scanners (CodeQL and Secret Scanning via gitleaks) were configured to trigger only on the `master` branch. However, the repository's default and active branch is `main` (as explicitly documented in SECURITY.md).
**Learning:** This is a silent but critical security gap. The repository had the "appearance" of being secured by automated tools, providing a false sense of security, but the tools were effectively disabled because they never triggered on the active codebase. This often happens when older templates or examples using `master` are copy-pasted into newer repositories where `main` is the standard.
**Prevention:** Always verify that security workflow branch triggers actually match the repository's active default branch. Security tools are only useful if they actually run on the code being merged.
