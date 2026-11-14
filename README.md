# FLARE-VM Installation and Troubleshooting Lab



## Project Overview



This project documents the setup, installation and troubleshooting of FLARE-VM, a Windows-based environment designed for malware analysis and reverse engineering.



The lab was built inside a Windows 10 virtual machine using Oracle VirtualBox.



During installation, several software packages failed because of dependency warnings, unavailable download sources, checksum mismatches and certificate-trust issues.



Rather than bypassing security checks, I investigated the errors, used PowerShell to troubleshoot installation problems, downloaded selected tools from official developer sources, and performed software integrity checks.



## Project Objectives



- Build a Windows malware-analysis environment.

- Install and configure FLARE-VM.

- Troubleshoot Chocolatey package installation failures.

- Practice PowerShell commands for system administration.

- Investigate software download and dependency errors.

- Calculate SHA-256 hashes to examine file integrity.

- Verify Authenticode digital signatures.

- Document technical findings and troubleshooting procedures.

- Practice Git and GitHub version control.



## Tools and Technologies



| Tool               | Purpose                           |

| ------------------ | --------------------------------- |

| Oracle VirtualBox  | Virtual machine management        |

| Windows 10         | Analysis operating system         |

| FLARE-VM           | Malware analysis environment      |

| Chocolatey         | Windows package management        |

| PowerShell         | Installation troubleshooting      |

| Git                | Version control                   |

| GitHub             | Project hosting and documentation |

| Recaf              | Java bytecode analysis            |

| EZViewer           | Document and file viewing         |

| VB Decompiler Lite | Visual Basic executable analysis  |

| RegCool            | Windows Registry inspection       |

| 010 Editor         | Hex editing and binary inspection |







## Key Activities



1. Created a Windows 10 virtual machine.

2. Installed FLARE-VM.

3. Investigated failed Chocolatey packages.

4. Troubleshot Node.js-related installation errors.

5. Investigated unavailable download sources.

6. Manually recovered selected software from official developer websites.

7. Inspected ZIP archives before extraction.

8. Calculated SHA-256 hashes.

9. Investigated Authenticode signatures and certificate chains.

10. Tested recovered applications.

11. Documented installation outcomes and lessons learned.



## Security Considerations



- Used official developer sources for manual downloads.

- Examined SHA-256 hashes.

- Investigated digital signature validity.

- Avoided bypassing checksum verification.

- Did not manually trust an untrusted root certificate.

- Kept malware-analysis activities separate from the host operating system.



## Project Status



The core FLARE-VM environment was installed and several initially failed packages were recovered.



Some package issues remained under investigation, including the HxD download failure and the RegCool certificate-trust warning.



## Learning Outcomes



This project provided practical experience with Windows administration, PowerShell troubleshooting, Chocolatey package management, software integrity verification, digital certificates, reverse-engineering tools and technical documentation.



## Disclaimer



This is an independent cybersecurity learning project. The environment was configured for educational and controlled malware-analysis activities.



