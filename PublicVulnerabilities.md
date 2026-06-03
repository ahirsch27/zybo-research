# All Known Public Vulnurabilities
_Organized by _

## 1\. BootROM Vulnerabilities

_Investigate:_

- _BootROM parsing flaws_
- _Secure boot bypasses_
- _Authentication weaknesses_
- _Image validation weaknesses_

_Known starting points:_

- _CVE-2021-44850_
- _SD boot image manipulation attacks_

CVEs Found:
1. [CVE-2021-44850](https://app.opencve.io/cve/CVE-2021-44850) (AMD)
2. [CVE-2010-0928](https://app.opencve.io/cve/CVE-2010-0928) (Gaisler, Openssl, Xilinx)
3. [CVE-2021-27208](https://app.opencve.io/cve/CVE-2021-27208) (Xilinx)
4. []() ()


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

CVEs Found:
1. [CVE-2022-23822](https://app.opencve.io/cve/CVE-2022-23822) (Xilinx)


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
