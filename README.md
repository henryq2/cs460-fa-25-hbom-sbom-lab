# CS 460/ECE 419 FA 25: HBOM/SBOM Supply Chain Lab

This repository is your working environment for the Module 8 lab.

You will:
1. Generate an SBOM for supplied firmware/code using Syft and Trivy.
2. Scan that SBOM for vulnerabilities using Grype.
3. Document top CVEs and map them to risk.
4. Identify HBOM components (chip, radio module, etc.) for your assigned physical device.
5. (Optional) Import your SBOM into Dependency-Track and screenshot the dashboard.

## Quick Start (Codespaces)

Click the badge below to launch this repo in a pre-configured Codespace.  
This gives you a Linux shell with all required tools already installed.

[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://github.com/codespaces/new?hide_repo_select=true&ref=main&repo=<REPO_ID_PLACEHOLDER>)

Once the Codespace opens:
```bash
syft --version
grype --version
trivy --version
cve-bin-tool --version
