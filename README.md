# CS 460/ECE 419 FA 25: Inside the Stack: Mapping Hardware and Software Bill of Materials Lab

This repository is your working environment for the Module 8: Inside the Stack: Mapping Hardware and Software Bill of Materials lab.

**HBOM vs. SBOM Explained**
*What’s the difference?* A **Software Bill of Materials (SBOM)** lists everything inside the code: The open-source libraries, packages, and dependencies that make up software components. A **Hardware Bill of Materials (HBOM)** lists everything on the board: The chips, sensors, microcontrollers, and modules that make up the physical device. Together, they provide end-to-end visibility across the digital and physical supply chain, which is essential for identifying vulnerabilities, counterfeit parts, and hidden dependencies.

**SBOM**:  
Purpose: Tracks software components, versions, and known CVEs.  
Focus: Software supply-chain risk (vulnerable libraries).  
Contents: Package names, versions, dependencies, licenses, CVEs.  
Common Formats:	SPDX, CycloneDX, Syft JSON.  
Key Users: Developers, vulnerability managers, software assurance teams.  
Tagline: *“What’s in the code.”*  

**HBOM**:  
Purpose: Tracks hardware components, part numbers, and suppliers.  
Focus: Hardware provenance and tampering risk (counterfeit or insecure chips).  
Contents: Chipsets, sensors, SoCs, communication modules, firmware IDs.  
Common Formats:	IPC-1752A, IPC-1754, or vendor-specific CSV/XML formats.  
Key Users: OEMs, supply-chain analysts, hardware security engineers.  
Tagline: *“What’s on the board.”*  

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
