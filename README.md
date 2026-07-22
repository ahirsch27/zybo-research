<a id="readme-top"></a>


<br />
<div align="center">
  <a href="https://github.com/irys-intern/zybo-research/tree/main/Images">
    <img width="128" height="90" alt="logo" src="https://github.com/user-attachments/assets/121d67a0-cd95-40be-9d2b-b1b9b7eb5f1c" />
  </a>

  <h3 align="center">Zynq-7000 Vulnerability Assessment</h3>

  <p align="center">
    A comprehensive security assessment and resource library of the AMD Zynq-7000 SoC — covering BootROM, secure boot, FPGA bitstream, TrustZone, side-channel attacks, and more.
    <br />
    <br />
    <a href="https://github.com/irys-intern/zybo-research/issues/new?labels=bug&template=bug-report---.md">Report Issue</a>
    &middot;
    <a href="https://github.com/irys-intern/zybo-research/issues/new?labels=enhancement&template=feature-request---.md">Request Addition</a>
  </p>
</div>

---

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

## Scope & Versioning


| Hardware | AMD Zynq-7000 Series (Zybo Z7-20, XC7Z020) |
| --- | --- |
| Toolchain | Vivado / Vitis ≤ 2024.1, Petalinux ≤ 2024.1 |
| OP-TEE | ≤ 4.10 |
| Vulnerabilities Documented | 26 |
| Research Domains | 10 of 10 ✅ Complete |
| Last Updated | July 6, 2026 |

## Built With

* [![GitHub](https://img.shields.io/badge/GitHub-%23121011.svg?logo=github&logoColor=white)](#)
* [![Visual Studio Code](https://custom-icon-badges.demolab.com/badge/Visual%20Studio%20Code-0078d7.svg?logo=visualstudiocode&logoColor=white)](#)
* [![Notion](https://img.shields.io/badge/Notion-000?logo=notion&logoColor=fff)](https://app.notion.com/p/Zynq-7000-Vulnerability-Assessment-382f2a6280d38122afcbc2af16791df3?source=copy_link)
* [![Claude](https://img.shields.io/badge/Claude-D97757?logo=claude&logoColor=fff)](#)
* [![Markdown](https://img.shields.io/badge/Markdown-%23000000.svg?logo=markdown&logoColor=white)](#)
* [![Windows](https://custom-icon-badges.demolab.com/badge/Windows-0078D6?logo=windows11&logoColor=white)](https://www.microsoft.com/en-us/windows)
---


## Assessment Summary

> *An executive security assessment and prioritized mitigation roadmap for the Zynq-7000, tailored for security managers and lead engineers to evaluate threats rapidly before a deployment decision.*

[View Assessment Summary](Zynq-7000%20Vulnerability%20Assessment/Assessment%20Summary.md)


## Threat Model

> *A foundational overview of the threat model's scope, attacker profiles, and risk assessment criteria, designed to help auditors and stakeholders understand the baseline assumptions and boundaries before evaluating findings.*

[View Threat Model](Zynq-7000%20Vulnerability%20Assessment/Threat%20Model.md)



## Vulnerability Database

> *A comprehensive, multi-indexed vulnerability catalog of all documented CVEs, advisories, and findings detailing CVSS scores, components, and exploit availability, structured for security analysts, engineers, and researchers to triage threats and check patch status.*

[View Vulnerability Database](Zynq-7000%20Vulnerability%20Assessment/Vulnerability%20Database%20287bad1d4fd04f06a08de35ef1a3358d.csv)


## Research Topics

> *A detailed, ten-part technical deep dive into major Zynq-7000 attack domains, covering everything from BootROM and FPGA bitstream security to side-channel attacks and fault injection, built to help penetration testers, researchers, and engineers analyze vulnerabilities and design security controls.*

[View Research Topics](Zynq-7000%20Vulnerability%20Assessment/Research%20Topics.md)



## Attack Surface Inventory

> *An attack surface mapping of the Zynq-7000 across physical interfaces, processing system, programmable logic, and the software stack, documenting vulnerabilities, risk levels, and mitigations for security architects and red teams assessing physical exposure.*

[View Attack Surface Inventory](Zynq-7000%20Vulnerability%20Assessment/Attack%20Surface%20Inventory.md)


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

**Avery Hirsch**
<br>*Cyber Security Research Intern (Summer 2026), Irys Technologies*

![Static Badge](https://img.shields.io/badge/Email%20Me-DC1027?style=plastic&logo=minutemailer&logoColor=black&logoSize=auto&color=DC1027&link=mailto%3Ahirsch_avery%40yahoo.com%3Fsubject%3DZynq-7000%2520Project%2520-%2520%255BInsert%2520Subject%2520Here%255D)
 [![LinkedIn](https://custom-icon-badges.demolab.com/badge/LinkedIn-0A66C2?logo=linkedin-white&logoColor=fff)](https://linkedin.com/in/ahirsch27) 
 [![GitHub](https://img.shields.io/badge/See%20My%20Other%20Projects-%23121011.svg?logo=github&logoColor=white)](https://github.com/ahirsch27)




---

<p align="right">~<a href="#readme-top">Back to Top</a>~</p>
