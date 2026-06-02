# Hybrid Enterprise Security Architecture & Penetration Testing Portfolio

## 🌐 Overview
This repository contains comprehensive technical documentation, deployment scripts, network topologies, and exploit verification capture logs for a series of advanced security engineering labs. 

The portfolio bridges the gap between **Defensive Infrastructure Hardening** and **Offensive Cyber Operations**. It demonstrates hands-on expertise in building secure Windows Server/Linux corporate directories, performing full-scale network reconnaissance, engineering automated vulnerability scans, and executing controlled exploitation/domain privilege escalation within fully sandboxed virtual labs.

---

## 🛠️ Portfolio Architecture & Core Domains

### 1. Enterprise Identity Management & Baseline System Hardening
* **Environment & Tools:** Windows Server 2019 Standard, Windows 10 Enterprise, VMware Workstation
* **Core Implementations:**
  * Provisioned **Active Directory Domain Services (AD DS)** and established verified cross-workstation domain connectivity.
  * Structured corporate user directories using **Organizational Units (OUs)**, nesting custom security group privileges, and configuring automated user tracking.
  * Deployed structural **Group Policy Objects (GPOs)** to enforce domain-wide account policies, restrict administrative exposure, and lock down unauthorized local tools.
  * Implemented strict access control restrictions on shared network volumes via NTFS permissions and file sharing audits.

### 2. Network Reconnaissance, Data Parsing & Asset Filtering
* **Environment & Tools:** Kali Linux, Vagrant, Packer Automated Provisioning, `nmap`, `netcat (nc)`, `ncat`
* **Core Implementations:**
  * Orchestrated multi-phase automated subnet mapping and structural host sweeps to discover live network interfaces.
  * Engineered Unix command-line parsing pipelines using `grep`, `cut`, and `sort -u` to extract and convert raw `.nmap` and `.gnmap` scan outputs into clean, target-focused host indexes.
  * Isolated network assets into functional profiles, dynamically segregating running web interfaces (`web.txt`), database layers (`mssql.txt`), and active OS instances (`windows.txt`) to build clear network topology landscapes.

### 3. Automated Vulnerability Auditing & Exploit Profiling
* **Environment & Tools:** Kali Linux, ProjectDiscovery `Nuclei` Engine, YAML Scripting
* **Core Implementations:**
  * Deployed the **Nuclei template engine** to conduct rapid, signature-based vulnerability indexing against critical network middleware.
  * Engineered and executed customized vulnerability scanning templates (e.g., `jenkins-fuzz.yaml`) to automate credential fuzzing and authentication testing.
  * Programmed compound **conditional matchers** (mapping HTTP `302 Found` response codes, isolating positive `Location:` flags, and utilizing negative matches on string structures like `loginError`) to dynamically verify successful system exposures without generating false positives.

### 4. Penetration Testing: Endpoint Exploitation & Domain Compromise
* **Environment & Tools:** Metasploit Framework (`msfconsole`), `NetExec (nxc)`, `Secretsdump`, `Evil-WinRM`, Oracle VirtualBox
* **Core Implementations:**
  * Leveraged auxiliary SMB scanners (`ms17_010 / DOUBLEPULSAR`) to systematically profile legacy target OS systems for remote code execution vulnerabilities.
  * Executed controlled exploitation of the **EternalBlue (MS17-010)** flaw to establish reverse shell sessions and dump system hashes.
  * Performed stealthy **User Hunting** across Windows targets using `NetExec` to track and isolate highly privileged Domain Administrator accounts without triggering local defenses.
  * Executed **Living-off-the-Land (LotL)** lateral movement via `Evil-WinRM`, abusing native PowerShell Remoting mechanics to operate purely in volatile memory (RAM) and bypass traditional EDR defenses.
  * Conducted a **DCSync attack** using Impacket's `secretsdump` tool, mimicking Domain Controller replication behavior via the `MS-DRSR` protocol to dump the entire Active Directory credential database (`ntds.dit`).

### 5. Network Security Monitoring & Real-Time Intrusion Detection
* **Environment & Tools:** Ubuntu Linux, Snort Engine Engine (NIDS Mode)
* **Core Implementations:**
  * Deployed and customized the **Snort IDS/IPS** engine across specialized network configurations (`snort.conf`).
  * Written and tuned custom string and protocol rules to intercept real-time packet streams, successfully logging and generating behavioral alerts against active network threat vectors (ICMP sweeps, fingerprinting, and application layer attacks).

### 6. Applied Cryptography & Core Infrastructure Protocols
* **Environment & Tools:** Linux Network Utilities (`dig`), `OpenPuff Steganography`, SMTP Infrastructure
* **Core Implementations:**
  * Analyzed structural cryptographic hashing digest algorithms (MD5 vs SHA-256/512) to demonstrate the **Avalanche Effect** and data fingerprinting mechanics for file integrity validation.
  * Audited critical internet backbone protocols using `dig +dnssec` to inspect cryptographic resource records (`RRSIG`, `DNSKEY`), confirming defenses against cache poisoning and domain redirection attacks.
  * Evaluated Simple Mail Transfer Protocol (SMTP) headers and Mail Transfer Agent (MTA) pathways to trace message routing validity and flag spoofing anomalies.

---

## 📂 Repository Structural Layout

```text
├── 01_enterprise_hardening/       # Active Directory, GPOs, and Access Control documentation
├── 02_network_reconnaissance/     # Subnet sweeps, Nmap scripts, and custom asset parsing filters
├── 03_vulnerability_automation/   # Nuclei vulnerability fuzzing templates and matcher configs
├── 04_penetration_testing/        # EternalBlue exploits, User Hunting, Evil-WinRM, and DCSync logs
├── 05_intrusion_detection/        # Snort engine parameters and custom detection rulesets
└── 06_protocol_cryptography/      # DNSSEC cryptographic signature mapping and steganography analysis# CyberSecurity-Projects
