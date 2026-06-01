# Fundamentals of Red Teaming & Offensive Security Lab

This repository serves as a foundational operational syllabus, tracking framework, and practical documentation hub for essential red teaming tactics. It covers the entry-level offensive lifecycle: reconnaissance, vulnerability assessment, active exploitation, persistence mechanisms, tool configuration, and professional reporting.

## 🎯 Core Objectives
* **Reconnaissance**: Master network architecture mapping and service discovery using active and passive enumeration.
* **Exploitation**: Validate infrastructure flaws via standard exploitation frameworks against vulnerable targets.
* **Post-Exploitation**: Simulate basic lateral movement, local credential harvesting, and persistent backdoor access.
* **Operational Documentation**: Map actions to the MITRE ATT&CK matrix and draft standard Rules of Engagement (RoE).

---

## 🧠 Theoretical Knowledge Mapping

### 1. Fundamentals of Red Teaming
* **Core Concepts**: Simulating adversary behaviors to stress-test defensive postures across the cyber attack lifecycle.
* **Framework Alignment**: Understanding tactical sequencing and standard categorization using the MITRE ATT&CK framework.
* **Resources**: TryHackMe Red Team Fundamentals | Cybrary Red Team Basics modules.

### 2. Reconnaissance and Information Gathering
* **Passive Enumeration**: Gathering OSINT data, WHOIS records, and domain leaks without direct target interaction.
* **Active Discovery**: Probing live targets via systematic network port scanning and service banner grabbing.
* **Tooling**: Nmap (Network Mapper), Maltego (OSINT graph analysis), theHarvester (Asset gathering).

### 3. Exploitation and Vulnerability Assessment
* **Vulnerability Analysis**: Scanning targets for known CVEs, identifying software bugs, and prioritizing risks.
* **Initial Access**: Crafting and delivering functional payloads to exploit discovered misconfigurations.
* **Tooling**: Metasploit Framework (Exploit deployment), OpenVAS / Greenbone (Vulnerability scanning).

### 4. Post-Exploitation and Persistence
* **Access Maintenance**: Establishing reliable, long-term backdoors and automated script execution persistence.
* **Data Maneuvers**: In-memory credential extraction and target host file transfers.
* **Tooling**: Mimikatz (LSASS dumping), Netcat (Raw TCP/UDP networking), PowerShell scripting.

### 5. Reporting and Red Team Operations
* **Operational Scope**: Defining strict boundary limitations, targets, and legally binding Rules of Engagement (RoE).
* **Technical Communication**: Documenting execution phases, attack paths, risk definitions, and remediation advice.

---

## 🧪 Practical Application Labs & Logs

### Lab 1: Network Scanning (Nmap)
* **Actions**: Conducted version scanning and script enumeration against target lab subnets to identify active, listening services.


| Port | Service | Version | Notes / Script Output |
|------|---------|---------|-----------------------|
| 21   | FTP     | vsftpd 2.3.4 | Potential backdoor vulnerability |

### Lab 2: Vulnerability Scanning (OpenVAS)
* **Actions**: Managed automated network vulnerability assessments against target hosts and validated exploit paths via Metasploit.


| Vulnerability | CVSS Score | Description | Exploit Verified? |
|---------------|------------|-------------|-------------------|
| VSFTPD Backdoor | 7.5 | Allows remote unauthenticated code execution | Yes (Metasploit) |

### Lab 3: Exploitation Practice (Metasploit)
* **Actions**: Deployed active exploit modules against exposed services to obtain initial system access and evaluated local file configurations for privilege escalation vectors.

```bash
# Example initial access routine
msfconsole
use exploit/unix/ftp/vsftpd_234_backdoor
set RHOSTS 192.168.1.x
exploit
```

### Lab 4: Post-Exploitation & Persistence
* **Actions**: Extracted dummy credentials out of runtime memory, configured scheduled baseline task execution scripts, and dropped interactive reverse shells.

```cmd
:: Credential dumping syntax used
mimikatz.exe "sekurlsa::logonpasswords" exit
```

### Lab 5: Malware Analysis (EICAR & Sandbox)
* **Actions**: Generated standardized EICAR anti-malware test strings, executed file reputation checks via VirusTotal, and evaluated telemetry reports from automated sandboxes.

### Lab 6: Password Security & Brute-Forcing (Hydra)
* **Actions**: Established high-entropy credential vaults using KeepPassXC and simulated online dictionary attacks using Hydra against unhardened authentication services.

### Lab 7: Security Assessment Reporting
* **Actions**: Formulated a standardized SANS-style security assessment report featuring an executive overview, visual attack graph paths, and technical remediation recommendations.

### Lab 8: Red Team Operations Infrastructure
* **Actions**: Diagrammed procedural flows in Draw.io, designed operational deployment checklists using Trello, and authored a formal mock Rules of Engagement document.

---

## 🗺️ MITRE ATT&CK Matrix Mapping


| Lifecycle Phase | Technique ID | Technique Name | Tool Used | Operational Context |
|-----------------|--------------|----------------|-----------|---------------------|
| Initial Access | T1190 | Exploit Public-Facing Application | Metasploit | Exploited vsftpd 2.3.4 service bug |
| Execution | T1059 | Command and Scripting Interpreter | PowerShell | Executed host collection scripts |
| Persistence | T1053.005 | Scheduled Task/Job: Scheduled Task | Windows Native | Scheduled persistent file generation |
| Credential Access| T1003 | OS Credential Dumping | Mimikatz | Dumped LSASS secrets from memory |

---
⚠️ **Disclaimer**: The documentation and scripts within this repository are hosted strictly for academic purposes, defensive validation, and authorized security auditing exercises. Unauthorized network testing is illegal.
