# Security Scanning

## Overview
This repository uses three types of security scanning integrated into the CI/CD pipeline. These scans provide layered security coverage throughout the development lifecycle.

### SAST (Static Analysis with CodeQL)
- Scans **source code** for vulnerabilities, analyzing code logic and patterns.
- Runs on **push to main branch** and on **Pull Requests** (as a blocking quality gate).
- Checks for: **Injection Flaws, logical errors, API misuse, and insecure code patterns.**
- Artifacts: See **GitHub Security tab** (Code scanning alerts).

### SCA (Dependency Check)
- Scans **third-party packages and libraries** for known security flaws.
- Runs on **push to main branch** and whenever **dependency files** (e.g., `requirements.txt`, `package.json`) change.
- Checks for: **Known CVEs** in dependencies and **outdated versions**.
- Artifacts: **sca-reports** (e.g., JSON, HTML reports).

### DAST (Live Application with ZAP)
- Tests the **running application** for vulnerabilities by simulating malicious attacks.
- Runs on **push to main branch** (typically after a successful deploy to a staging environment).
- Checks for: **Missing security headers, runtime misconfigurations, and web application flaws (e.g., injection, path traversal) via black-box testing.**
- Artifacts: **zap-baseline-reports, zap-fullscan-reports** (e.g., HTML, JSON, Markdown reports).

## Understanding Results
Refer to the **SCAN_ANALYSIS.md** document for a detailed breakdown of findings. All non-Informational alerts must be addressed: **FAIL-NEW (High)** should be fixed immediately; **WARN-NEW (Medium/Low)** must be prioritized for remediation or documented as an acceptable risk.

## Reporting Vulnerabilities
Please email **security@example.com**