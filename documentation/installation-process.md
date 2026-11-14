# FLARE-VM Installation Process



## 1. Lab Environment



FLARE-VM was installed in an isolated Windows 10 virtual machine using Oracle VirtualBox.



### Virtual Machine Configuration



| Component               | Configuration         |

| ----------------------- | --------------------- |

| Virtualization Platform | Oracle VirtualBox     |

| Guest Operating System  | Windows 10            |

| Allocated RAM           | 6 GB                  |

| Virtual CPUs            | 2                     |

| Virtual Disk            | Dynamically allocated |

| Virtual Disk Capacity   | 75.92 GB              |

| Host RAM                | 16 GB                 |



### Lab Purpose



The purpose of this lab was to establish a dedicated Windows environment for malware analysis and reverse engineering.



The virtual machine was kept separate from the host system to maintain isolation between the analysis environment and personal host data.



## 2. FLARE-VM Installation



FLARE-VM was installed inside the Windows 10 virtual machine using its installation process.



The installer completed its execution and presented a prompt to press Enter to continue or exit.



However, the installation report identified several individual package failures. Therefore, successful completion of the installer wrapper did not mean that every analysis tool had installed successfully.



### Installation Challenges



The initial installation report identified several categories of errors:



- Node.js dependency and warning-related errors.

- HTTP 502 and HTTP 404 download failures.

- SHA-256 checksum mismatches.

- Python package installation errors.

- Certificate-trust issues.



These errors required further investigation rather than blindly bypassing installation checks.



## 3. Troubleshooting Failed Packages



After the initial FLARE-VM installation, I reviewed the installation report to identify packages that had failed.



The original report listed 12 failed packages:



1. obfuscator-io-deobfuscator.vm

2. malware-jail.vm

3. asar.vm

4. js-beautify.vm

5. HxD

6. ezviewer.vm

7. js-deobfuscator.vm

8. pkg-unpacker.vm

9. recaf.vm

10. angr.vm

11. regcool.vm

12. vb-decompiler-lite.vm



### 3.1 Node.js-Related Installation Errors



Several packages encountered errors associated with Node.js dependencies and experimental warning messages.



The installed Node.js environment was checked using:



- `node --version`

- `npm --version`

- `where.exe node`



Node.js version 23.1.0 and npm version 10.9.0 were identified.



The following PowerShell environment variable was used as an operational workaround:



`$env:NODE_OPTIONS="--disable-warning=ExperimentalWarning"`



Selected package installation attempts were then repeated.



Six Node.js-related packages were subsequently confirmed in the Chocolatey package list:



- asar.vm

- js-beautify.vm

- obfuscator-io-deobfuscator.vm

- malware-jail.vm

- js-deobfuscator.vm

- pkg-unpacker.vm



The workaround was associated with successful retries, although the exact underlying cause of the original failures was not conclusively established.



### 3.2 Download and Checksum Errors



Other packages encountered download failures or checksum mismatches.



Rather than disabling integrity checks, I investigated alternative downloads from official developer sources where available.



### 3.3 Security Verification



For manually obtained tools, I performed checks that included:



- Inspecting ZIP archive contents before extraction.

- Calculating SHA-256 hashes.

- Checking Authenticode digital signatures.

- Examining certificate trust information.

- Launching selected applications to confirm basic functionality.



## 4. Package Recovery Results

Following the troubleshooting process, the initial package failures had different outcomes.

| Package | Outcome |
|---|---|
| asar.vm | Successfully installed |
| js-beautify.vm | Successfully installed |
| obfuscator-io-deobfuscator.vm | Successfully installed |
| malware-jail.vm | Successfully installed; npm reported dependency vulnerabilities |
| js-deobfuscator.vm | Confirmed in Chocolatey package list |
| pkg-unpacker.vm | Confirmed in Chocolatey package list |
| angr.vm | Confirmed in Chocolatey package list |
| EZViewer | Manually downloaded, extracted and Authenticode signature verified |
| Recaf | Manually downloaded and launched successfully; alpha/SNAPSHOT build |
| VB Decompiler Lite | Manually downloaded, extracted and Authenticode signature verified |
| RegCool | Manually downloaded and extracted; certificate trust remained unresolved |
| HxD | Download remained unsuccessful because the official download endpoint returned HTTP 502 |

### Outstanding Security Considerations

RegCool presented a self-signed certificate that was not trusted by the Windows certificate store. I did not add the certificate to the trusted root store.

The malware-jail installation also reported 49 dependency vulnerabilities: 10 moderate, 23 high and 16 critical.

These findings were documented rather than ignored.



## 5. Lessons Learned

This lab provided practical experience in troubleshooting a Windows-based malware analysis environment.

Key lessons included:

1. **Installation troubleshooting:** An installer completing successfully does not guarantee that every individual package was installed.
2. **Dependency management:** Software dependencies can affect package installation and functionality.
3. **File integrity:** SHA-256 hashes help identify whether downloaded files match expected values, although a hash alone does not establish publisher authenticity.
4. **Digital signatures:** Authenticode verification helps assess software publisher identity and certificate trust.
5. **Security awareness:** Checksum mismatches and untrusted certificates should be investigated rather than bypassed.
6. **Documentation:** Recording errors, troubleshooting steps and outcomes makes technical work easier to review and reproduce.



## 6. Conclusion

The FLARE-VM installation and troubleshooting exercise improved my practical understanding of Windows administration, package management, software verification and malware-analysis environment preparation.

Although several initially failed packages were recovered, some issues remained unresolved. These findings were documented to maintain an accurate record of the lab.

