# **Security Research Requirements: Zybo Z7 / Zynq-7000 Vulnerability Assessment**

# Objective

Produce a comprehensive technical report identifying all publicly known vulnerabilities, attack vectors, security weaknesses, and mitigations applicable to:

- Zybo Z7 development boards
- Zynq-7000 SoC devices
- Zynq boot chain and secure boot implementation
- FPGA configuration and bitstream security
- ARM Cortex-A9 processing system
- TrustZone implementation
- Linux and bare-metal deployments on Zynq
- Debug and manufacturing interfaces (JTAG, UART, SD, QSPI, USB, Ethernet)
- Third-party IP blocks commonly deployed on Zynq systems

The report should focus on practical security risk rather than merely cataloging CVEs.

# Deliverables

## Deliverable 1: tldr Summary

Include:

- Overall security posture of Zybo Z7
- Most critical attack paths
- High-risk vulnerabilities
- Recommended mitigations
- Residual risk after mitigation

## Deliverable 2: Attack Surface Inventory

Document all attack surfaces.

### **Physical Interfaces**

- JTAG
- UART
- USB
- SD card
- QSPI flash
- Ethernet
- PMOD connectors
- FMC/Pmod attached peripherals
- Power/reset circuitry

### **Processing System (PS)**

- ARM Cortex-A9 cores
- MMU
- TrustZone
- DMA engines
- Interrupt controller
- DDR controller

### **Programmable Logic (PL)**

- Bitstream loading
- Partial reconfiguration
- User IP blocks
- AXI interconnects

### **Software**

- BootROM
- FSBL
- U-Boot
- Linux kernel
- Device drivers
- Root filesystem

## Deliverable 3: Known Vulnerabilities

For each vulnerability provide:

- Identifier (CVE, paper, advisory, or vulnerability name)
- Affected components
- Attack prerequisites
- Impact
- Public exploit availability
- Mitigation
- References

Include a table summarizing all findings.

# Mandatory Research Topics

## 1\. BootROM Vulnerabilities

Investigate:

- BootROM parsing flaws
- Secure boot bypasses
- Authentication weaknesses
- Image validation weaknesses

Known starting points:

- CVE-2021-44850
- SD boot image manipulation attacks

## 2\. Secure Boot Attacks

Investigate:

- Secure boot implementation
- RSA authentication weaknesses
- AES bitstream protection
- Boot image manipulation
- Key storage methods

Review:

- AMD secure boot documentation
- Academic papers targeting Zynq secure boot

### 3\. FSBL Vulnerabilities

Investigate:

- First Stage Boot Loader weaknesses
- Open-source FSBL vulnerabilities
- Authentication bypass opportunities
- Memory corruption issues

Known starting point:

- WOOT 2024 "Achilles Heel in Secure Boot"

## 4\. FPGA Bitstream Security

Research:

- Bitstream extraction
- Bitstream cloning
- Bitstream modification
- Reverse engineering attacks
- Side-channel attacks

Include:

- Starbleed-related research
- Encrypted bitstream attacks
- Key recovery attacks

## 5\. TrustZone Weaknesses

Investigate:

- Misconfiguration risks
- Secure/non-secure boundary failures
- DMA bypass attacks
- Shared resource attacks
- Covert channels

## 6\. Debug Interface Risks

Investigate:

- JTAG access
- Debug Access Port (DAP)
- Manufacturing mode exposure
- Secure vs non-secure boot behavior

Determine:

- Whether JTAG can be disabled
- Whether JTAG can be re-enabled
- Post-boot debug exposure

## 7\. Side-Channel Attacks

Investigate:

- Differential Power Analysis
- Timing attacks
- Electromagnetic leakage
- Key extraction attacks

Document any demonstrated attacks against:

- Zynq-7000
- Cortex-A9
- FPGA configuration engines

## 8\. Fault Injection Attacks

Research:

- Voltage glitching
- Clock glitching
- Electromagnetic fault injection
- Secure boot bypass through fault injection

## 9\. Linux Security

Investigate:

- Kernel vulnerabilities affecting Zynq deployments
- Driver vulnerabilities
- DMA attacks
- FPGA manager security
- Device-tree attack vectors

## 10\. Supply Chain and IP Risks

Investigate:

- Malicious FPGA IP
- Third-party AXI peripherals
- Hardware Trojans
- Open-source IP security concerns

# Final Deliverable

Produce:

- GitHub wiki page for your findings
- tldr summary