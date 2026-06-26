# **Zybo Z7 / Zynq-7000 Vulnerability Assessment**

This project serves as a comprehensive library identifying all publicly known vulnerabilities, attack vectors, security weaknesses, and mitigations applicable to:

- Zybo Z7 Development Boards
- Zynq-7000 SoC Devices
- Zynq Boot Chain and Secure Boot Implementation
- FPGA configuration and Bitstream Security
- ARM Cortex-A9 Processing System
- TrustZone Implementation
- Linux and Bare-Metal Deployments on Zynq
- Debug and Manufacturing Interfaces (JTAG, UART, SD, QSPI, USB, Ethernet)
- Third-party IP Blocks Commonly Deployed on Zynq Systems

#
# **TLDR:** 

## Overall Security Posture of Zybo Z7
The Zybo Z7 / Zynq-7000 presents a **moderate-to-high risk profile** for deployed systems. The device lacks hardware-level resistance to physical attacks. Secure boot is optional and must be explicitly enabled via eFUSE programming. When misconfigured or running legacy toolchain versions, multiple high-severity authentication bypasses are possible.

> _This rating assumes an attacker with physical access and moderate hardware security expertise. Remote-only attackers face a significantly reduced attack surface, limited primarily to the Linux network stack and any exposed services._


## Most Critical Attack Paths

1. **Physical JTAG access** — full debug control when DFT eFUSEs are not blown
    - CVE: eFUSE Volatile Mode Override
2. **SD/NAND boot image manipulation** — bypasses BootROM validation with no crypto knowledge required
    - CVE-2021-44850
    - CVE-2021-27208
3. **FSBL authentication bypass via Starbleed** — affects toolchain versions 2021.2–2022.1 specifically
    - CVE-2022-23822
4. **Bitstream decryption via side-channel power analysis** — no hardware countermeasure exists
    - Academic Paper eprint 2016/249
5. **TrustZone misconfiguration** — allows Non-Secure World access to Secure World memory regions
    - CVE-2026-33317
    - CVE-2026-40290
    - CVE-2026-33662
    - CVE-2023-41325

## High-Risk Vulnerabilities

| Identifier | Title | CVSS | Exploit | Mitigation |
| --- | --- | --- | --- | --- |
| CVE-2025-54520 | Voltage/Clock Glitch Attack on Artix-7 | 8.6 (v4.0) | Unproven | ❌ None |
| Design Advisory 76171 | Weak AES/HMAC Key Seed in Bootgen | 7.4 (v3.1) | Unproven | ⚠️ Workaround |
| CVE-2021-44850 | SD Boot Overflow in BootROM | 6.8 (v3.1) | PoC | ⚠️ Workaround |
| CVE-2021-27208 | Buffer Overflow in BootROM/FSBL NAND Driver | 6.8 (v3.1) | PoC | ⚠️ Workaround |
| CVE-2022-23822 | Starbleed — FSBL Authentication Attack | 6.8 (v3.1) | PoC | ✅ Patched |


## Recommended Mitigations

**Do before deployment — blocking**

1. **Program all security-relevant eFUSEs** — one-time programmable and irreversible; test in a non-production environment first:
    - `RSA_EN` — enables RSA authentication enforcement
    - `AES_EN` — enables AES encryption enforcement
    - `JTAG_DIS` — disables JTAG in all boot modes
    - `DFT_JTAG_DISABLE` — disables ARM DAP and PL TAP in DFT mode
    - `DFT_MODE_DISABLE` — prevents SoC from entering DFT boot mode entirely
2. **Use toolchain 2022.1 or later** — never deploy on 2018.2 or earlier without manual authentication fixes for U-Boot (DA 71436, DA 71437) and FSBL (DA 71225, DA 71292)
3. **Supply your own AES and RSA keys** — never use Bootgen-generated keys in production; they are seeded with date/time and cryptographically weak (DA 76171)

**Ongoing operational controls**

1. **Physically secure all debug and boot interfaces** — restrict access to JTAG headers, UART console, and SD card slot; consider potting or tamper-evident enclosures
2. **Maintain OP-TEE patch currency** — apply all optee_os releases and monitor OP-TEE security advisories for new CVEs

## Residual Risk After Mitigation

**Bottom line:** Physical side-channel attacks (DPA, EMFI, voltage glitching) remain viable for a sophisticated attacker with sustained physical access even after all software and eFUSE mitigations are applied. The Zynq-7000 has **no hardware-level countermeasures** against these attacks — CVE-2025-54520 has no available mitigation from AMD.

**Residual risk disposition:** Accepted. Primary remaining defenses are system-level physical controls — tamper-evident enclosures, active tamper detection, restricted facility access, and monitored deployment environments. Any deployment where an adversary could obtain unsupervised physical access for an extended period should be treated as a higher-risk scenario requiring additional compensating controls.


# **Reference Materials**

## Getting Started

*Start with these three documents before anything else: **UG585** for hardware registers and security architecture, **UG821** for secure boot and eFUSE programming, and **UG1019** for TrustZone configuration. Everything else in this page is referenced from those three.*

- [UG585 — Zynq-7000 Technical Reference Manual](https://docs.amd.com/r/en-US/ug585-zynq-7000-SoC-TRM)
- [UG821 — Zynq-7000 Software Developers Guide](https://docs.amd.com/r/en-US/ug821-zynq-7000-swdev)
- [UG1019 — Programming ARM TrustZone on Zynq-7000](https://docs.amd.com/v/u/en-US/ug1019-zynq-trustzone)

---

## AMD / Xilinx Official Documentation

**Essential**

1. [Zybo Z7 Board Reference Manual](https://digilent.com/reference/_media/reference/programmable-logic/zybo-z7/zybo-z7_rm.pdf) — Hardware schematic, pinout, interface locations, and power supply design. Essential for identifying physical attack surfaces (JTAG headers, UART, SD slot, PMOD). *Used by: Topics 1, 6, 7, 8*
2. [Zynq-7000 SoC Software Developers Guide UG821](https://docs.amd.com/r/en-US/ug821-zynq-7000-swdev) — Secure boot configuration, eFUSE programming, key management, FSBL, U-Boot, and Linux bring-up. *Used by: Topics 1, 2, 3, 4, 6*
3. [Zynq-7000 SoC Technical Reference Manual UG585](https://docs.amd.com/r/en-US/ug585-zynq-7000-SoC-TRM) — Definitive hardware reference for all registers, peripherals, and security architecture (SLCR, TZPC, XMPU, DEVCFG, eFUSE). *Used by: Topics 2, 3, 4, 5, 6, 7*
4. [Programming ARM TrustZone on Zynq-7000 UG1019](https://docs.amd.com/v/u/en-US/ug1019-zynq-trustzone) — Step-by-step TrustZone configuration including SLCR, TZPC, XMPU, and OP-TEE integration. The primary reference for TrustZone hardening. *Used by: Topic 5*
5. [Zynq-7000 Design Advisory Master Answer Record 47915](https://adaptivesupport.amd.com/s/article/47915?language=en_US) — Master index of all Zynq-7000 design advisories. Start here when searching for known hardware errata and security advisories. *Used by: All topics*

**Supplementary**

1. [Bootgen User Guide UG1283](https://docs.amd.com/r/en-US/ug1283-bootgen-user-guide) — Bootgen tool for creating boot images, configuring encryption/authentication, managing key files, and programming eFUSEs. *Used by: Topics 2, 3*
2. [Petalinux Tools Reference Guide UG1144](https://docs.amd.com/r/en-US/ug1144-petalinux-tools-reference-guide) — Building Linux-based systems on Zynq-7000 using Petalinux; kernel configuration, rootfs hardening, and default service configuration. *Used by: Topic 9*
3. [Zynq-7000 DC/AC Switching Characteristics DS187](https://docs.amd.com/v/u/en-US/ds187-XC7Z010-XC7Z020-Data-Sheet) — Electrical characteristics including power supply specifications and timing. Relevant for fault injection attack characterization. *Used by: Topic 8*
4. [Standalone Library BSP and Libraries UG643](https://docs.amd.com/r/en-US/oslib_rm) — Bare-metal BSP libraries for Zynq-7000. Relevant for FSBL and bare-metal security analysis. *Used by: Topic 3*
5. [Zynq-7000 SoC Solution Center 52512](https://adaptivesupport.amd.com/s/article/52512?language=en_US) — AMD's central support hub for Zynq-7000 known issues, patches, and workarounds. *Used by: All topics*
6. [Zynq-7000 Design Overview Hub DH239](https://docs.amd.com/v/u/en-US/dh0050-zynq-7000-design-overview-hub) — High-level design guide covering system architecture, PS-PL integration, and AXI interconnect topology. *Used by: Topic 10*
7. [AMD Product Security Page](https://www.amd.com/en/resources/product-security.html) — Central index for all AMD security bulletins. Monitor for new Zynq-7000 advisories. *Used by: All topics*

---

## AMD Design Advisories

1. [Design Advisory 71225](https://adaptivesupport.amd.com/s/article/71225) — FSBL authenticates boot image in external DDR rather than OCM, enabling time-of-check/time-of-use attacks. *Used by: Topic 3*
2. [Design Advisory 71292](https://adaptivesupport.amd.com/s/article/71292) — FSBL performs security operations based solely on partition header content without independent validation (≤ 2018.2). *Used by: Topic 3*
3. [Design Advisory 71436](https://adaptivesupport.amd.com/s/article/71436) — U-Boot does not use the PPK verified and stored by BootROM, breaking the chain of trust (≤ 2018.2). *Used by: Topics 2, 3*
4. [Design Advisory 71437](https://adaptivesupport.amd.com/s/article/71437) — U-Boot does not authenticate the partition header, allowing unauthenticated partition loading (≤ 2018.2). *Used by: Topics 2, 3*
5. [Design Advisory 76125](https://adaptivesupport.amd.com/s/article/76125) — Bootgen fails to replace existing authentication key files when regenerating keys (≤ 2020.3). *Used by: Topic 2*
6. [Design Advisory 76171](https://adaptivesupport.amd.com/s/article/76171) — Bootgen generates AES and HMAC keys seeded with system date/time, producing weak keys. *Used by: Topic 2*
7. [Design Advisory 76964](https://adaptivesupport.amd.com/s/article/76964) — AMD advisory for CVE-2021-44850 (SD Boot overflow in BootROM). *Used by: Topic 1*
8. [Design Advisory 76974](https://adaptivesupport.amd.com/s/article/76974) — AMD advisory for CVE-2022-23822 (Starbleed FSBL authentication attack). *Used by: Topic 3*
9. [Design Advisory 76201](https://adaptivesupport.amd.com/s/article/76201) — AMD advisory for CVE-2021-27208 (BootROM/FSBL NAND buffer overflow). *Used by: Topic 1*
10. [Security Bulletin AMD-SB-8018](https://www.amd.com/en/resources/product-security/bulletin/AMD-SB-8018.html) — AMD security bulletin for CVE-2025-54520 (voltage/clock glitch attack on Artix-7). No mitigation available. *Used by: Topics 4, 8*

---

## ARM Documentation

1. [ARM Cortex-A Series Programmer's Guide DEN0013](https://developer.arm.com/documentation/den0013/0400) — Comprehensive ARMv7-A guide including memory model, exception handling, MMU, and security extensions. *Used by: Topics 5, 7, 9*
2. [ARMv7-A Security Extensions](https://developer.arm.com/documentation/den0013/0400/Security/TrustZone-hardware-architecture) — TrustZone Hardware Architecture — TrustZone hardware implementation on ARMv7-A — the architecture used by the Cortex-A9 in Zynq-7000. *Used by: Topic 5*
3. [ARM Spectre / Meltdown Vulnerability Documentation 110280](https://developer.arm.com/documentation/110280/latest) — ARM's official analysis of Spectre and Meltdown variants across ARM processor families, including Cortex-A9 specific guidance. *Used by: Topic 9*

---

## Academic and Security Research Papers

1. [Fault-Based Attack on RSA (DATE 2010)](https://web.eecs.umich.edu/~valeria/research/publications/DATE10RSA.pdf) — Demonstrates a fault-based attack against RSA authentication in OpenSSL 0.9.8i and Xilinx RSA implementations. Foundational reference for RSA fault attacks. *Used by: Topic 7 · CVE-2010-0928*
2. [Decryption Verification Side-Channel Attacks on FPGA Bitstream Encryption (eprint 2016/249)](https://eprint.iacr.org/2016/249.pdf) — Demonstrates practical DPA extraction of AES bitstream encryption keys from Artix-7 / Zynq-7000 FPGA configuration engines. The primary FPGA side-channel reference. *Used by: Topics 4, 7*
3. [SoK: Understanding the Prevailing Security Vulnerabilities in TrustZone-Assisted TEE Systems (IEEE 2020)](https://ieeexplore.ieee.org/document/9152801) — Systematization of knowledge covering all major TrustZone vulnerability classes including configuration errors, OP-TEE bugs, and supply chain risks. *Used by: Topics 5, 10*
4. [Spectre Attack Paper](https://spectreattack.com/spectre.pdf) — Original Spectre vulnerability disclosure covering Bounds Check Bypass (V1) and Branch Target Injection (V2) on out-of-order processors including ARM Cortex-A. *Used by: Topic 9 · CVE-2017-5753, CVE-2017-5715, CVE-2018-3693*
5. [WOOT 2024 — "Achilles Heel in Secure Boot"](https://www.usenix.org/conference/woot24) — Mitev et al. Demonstrates partition header confusion attacks (TOCTOU) against the Zynq-7000 FSBL authentication chain. Findings documented in Topic 3. *Used by: Topic 3*

---

## Tools and Exploit References

1. [dev-zzo PoC Gist](https://gist.github.com/dev-zzo/f9eb667729dc9f9a537afb2a77bb6161) — CVE-2021-44850 and CVE-2021-27208 — PoC exploit demonstrating SD boot overflow and NAND buffer overflow in the Zynq-7000 BootROM. *Used by: Topic 1*
2. [Spectre Attack PoC](https://github.com/Eugnis/spectre-attack) — Working Spectre V1 / V2 proof-of-concept on ARM and x86. *Used by: Topic 9 · CVE-2017-5753, CVE-2017-5715*
3. [Spectre / Meltdown Checker Script](https://github.com/speed47/spectre-meltdown-checker) — Shell script detecting Spectre, Meltdown, and related CPU speculation vulnerabilities on a running system. Run on deployed Petalinux systems to verify mitigation status. *Used by: Topic 9*
4. [Starbleed FCCM 2022 Paper](https://www.computer.org/csdl/proceedings-article/fccm/2022/09786118/1DUdQjQTLDG) — Academic paper demonstrating the Starbleed FSBL authentication bypass (CVE-2022-23822) with full technical methodology. *Used by: Topic 3 · CVE-2022-23822*
5. [ChipWhisperer Documentation](https://chipwhisperer.readthedocs.io/) — Open-source power analysis and fault injection platform commonly used for DPA and voltage glitch attacks against FPGA targets including Zynq-7000 / Artix-7. *Used by: Topics 7, 8*

---

## CVE and Vulnerability Databases

1. [NVD / CVE Database](https://www.cve.org/) — Authoritative CVE records, CVSS scores, and official vulnerability descriptions. *Used by: All topics*
2. OpenCVE — CVE search and monitoring with vendor filtering. Search `xilinx` and `linaro` (OP-TEE) for new advisories. *Used by: All topics*
3. [EU Vulnerability Database (EUVD)](https://euvd.enisa.europa.eu/homepage) — ENISA's European vulnerability database. Cross-reference source for EUVD identifiers used in this assessment. *Used by: All topics*
4. [Vulners](https://vulners.com/) — Aggregated vulnerability intelligence covering CVEs, vendor advisories, and exploit code references. *Used by: All topics*
5. [GitHub Security Advisories — OP-TEE](https://github.com/OP-TEE/optee_os/security/advisories) — Primary source for all OP-TEE CVEs and patch releases. *Used by: Topic 5*
6. [OP-TEE OS Releases](https://github.com/OP-TEE/optee_os/releases) — Track new optee_os releases for patches to currently unmitigated CVEs. *Used by: Topic 5*

---