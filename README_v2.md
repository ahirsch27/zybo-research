<!-- Improved compatibility of back to top link: See: https://github.com/othneildrew/Best-README-Template/pull/73 -->
<a id="readme-top"></a>

<!-- PROJECT SHIELDS -->
[![Stargazers][stars-shield]][stars-url]
[![Issues][issues-shield]][issues-url]
[![LinkedIn][linkedin-shield]][linkedin-url]

<!-- PROJECT LOGO -->
<br />
<div align="center">
  <a href="https://github.com/irys-intern/zybo-research/tree/main/Images">
    <img src="images/logo.png" alt="Logo" width="128" height="90">
  </a>

  <h3 align="center">Zynq-7000 Vulnerability Assessment</h3>

  <p align="center">
    A comprehensive security assessment of the AMD Zynq-7000 SoC — covering BootROM, secure boot, FPGA bitstream, TrustZone, side-channel attacks, and more.
    <br />
    <a href="https://github.com/irys-intern/zybo-research"><strong>Explore the docs »</strong></a>
    <br />
    <br />
    <a href="https://github.com/irys-intern/zybo-research/issues/new?labels=bug&template=bug-report---.md">Report Issue</a>
    &middot;
    <a href="https://github.com/irys-intern/zybo-research/issues/new?labels=enhancement&template=feature-request---.md">Request Addition</a>
  </p>
</div>

---

<!-- TABLE OF CONTENTS -->
<details>
  <summary>Table of Contents</summary>
  <ol>
    <li><a href="#scope--versioning">Scope &amp; Versioning</a></li>
    <li><a href="#assessment-summary">Assessment Summary</a></li>
    <li><a href="#threat-model">Threat Model</a></li>
    <li><a href="#vulnerability-database">Vulnerability Database</a></li>
    <li><a href="#research-topics">Research Topics</a></li>
    <li><a href="#attack-surface-inventory">Attack Surface Inventory</a></li>
    <li><a href="#reference-materials">Reference Materials</a></li>
    <li><a href="#contributing">Contributing</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

---

<!-- SCOPE & VERSIONING -->
## Scope & Versioning


| Hardware | AMD Zynq-7000 Series (Zybo Z7-20, XC7Z020) |
| --- | --- |
| Toolchain | Vivado / Vitis ≤ 2024.1, Petalinux ≤ 2024.1 |
| OP-TEE | ≤ 4.10 |
| Vulnerabilities Documented | 26 |
| Research Domains | 10 of 10 ✅ Complete |
| Last Updated | July 6, 2026 |

---

<!-- ASSESSMENT SUMMARY -->
## Assessment Summary

> *An executive security assessment and prioritized mitigation roadmap for the Zynq-7000, tailored for security managers and lead engineers to evaluate threats rapidly before a deployment decision.*

[View Assessment Summary](Zynq-7000%20Vulnerability%20Assessment/Assessment%20Summary.md)

---

<!-- THREAT MODEL -->
## Threat Model

> *A foundational overview of the threat model's scope, attacker profiles, and risk assessment criteria, designed to help auditors and stakeholders understand the baseline assumptions and boundaries before evaluating findings.*

[View Threat Model](Zynq-7000%20Vulnerability%20Assessment/Threat%20Model.md)


---

<!-- VULNERABILITY DATABASE -->
## Vulnerability Database

> *A comprehensive, multi-indexed vulnerability catalog of all documented CVEs, advisories, and findings detailing CVSS scores, components, and exploit availability, structured for security analysts, engineers, and researchers to triage threats and check patch status.*

[View Vulnerability Database](Zynq-7000%20Vulnerability%20Assessment/Vulnerability%20Database%20287bad1d4fd04f06a08de35ef1a3358d.csv)

---

<!-- RESEARCH TOPICS -->
## Research Topics

> *A detailed, ten-part technical deep dive into major Zynq-7000 attack domains, covering everything from BootROM and FPGA bitstream security to side-channel attacks and fault injection, built to help penetration testers, researchers, and engineers analyze vulnerabilities and design security controls.*

[View Research Topics](Zynq-7000%20Vulnerability%20Assessment/Research%20Topics.md)

---

<!-- ATTACK SURFACE INVENTORY -->
## Attack Surface Inventory

> *An attack surface mapping of the Zynq-7000 across physical interfaces, processing system, programmable logic, and the software stack, documenting vulnerabilities, risk levels, and mitigations for security architects and red teams assessing physical exposure.*

[View Attack Surface Inventory](Zynq-7000%20Vulnerability%20Assessment/Attack%20Surface%20Inventory.md)

---

<!-- REFERENCE MATERIALS -->
## Reference Materials

> *A curated library of official AMD/Xilinx documentation, ARM architecture guides, academic papers, design advisories, and public exploit references, annotated with cross-references to assist researchers, engineers, and analysts verifying security configurations.*

[View Reference Materials](Zynq-7000%20Vulnerability%20Assessment/Reference%20Materials.md)

---

## Contributing

Contributions are welcome. If you have a finding to add, please fork the repo and open a pull request. You can also open an issue with the tag `enhancement`.

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/NewFinding`)
3. Commit your Changes (`git commit -m 'Add finding: CVE-XXXX-XXXXX'`)
4. Push to the Branch (`git push origin feature/NewFinding`)
5. Open a Pull Request

---

## Contact

Avery Hirsch - averyhirsch@irystechnologies.com

Project Link: [https://github.com/irys-intern/zybo-research](https://github.com/irys-intern/zybo-research)

---

<p align="right">~<a href="#readme-top">Back to Top</a>~</p>

<!-- MARKDOWN LINKS & IMAGES -->
[stars-shield]: https://img.shields.io/github/stars/irys-intern/zybo-research.svg?style=for-the-badge
[stars-url]: https://github.com/irys-intern/zybo-research/stargazers
[issues-shield]: https://img.shields.io/github/issues/irys-intern/zybo-research.svg?style=for-the-badge
[issues-url]: https://github.com/irys-intern/zybo-research/issues
[linkedin-shield]: https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555
[linkedin-url]: https://linkedin.com/in/ahirsch27
