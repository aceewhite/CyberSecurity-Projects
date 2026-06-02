Hybrid Enterprise Security Architecture & Penetration Testing Portfolio
=======================================================================

Overview
--------

Technical documentation and lab artifacts covering Active Directory hardening, network reconnaissance, automated vulnerability scanning, and post-exploitation — built across VMware/VirtualBox environments on Windows Server 2019 and Kali Linux.

Portfolio Architecture & Core Domains
-------------------------------------

1\. Enterprise Identity Management & Baseline System Hardening
--------------------------------------------------------------

**Environment & Tools:** Windows Server 2019 Standard, Windows 10 Enterprise, VMware Workstation

*   Provisioned AD DS and verified domain connectivity across multiple workstations.
    
*   Built OU hierarchy with nested security groups to delegate least-privilege access across 3 simulated departments.
    
*   Configured GPOs to enforce password policy, disable USB storage, and block unapproved executables domain-wide.
    
*   Restricted shared network volume access via NTFS permissions and enabled file sharing audits.
    

2\. Network Reconnaissance, Data Parsing & Asset Filtering
----------------------------------------------------------

**Environment & Tools:** Kali Linux, Vagrant, Packer, nmap, netcat, ncat

*   Ran phased nmap subnet sweeps to enumerate live hosts, open ports, and OS fingerprints across the lab range.
    
*   Parsed .gnmap output with grep/cut/sort -u to auto-generate target lists segmented by service (web.txt, mssql.txt, windows.txt).
    
*   Profiled discovered assets by role to build a working network topology before active exploitation.
    

3\. Automated Vulnerability Auditing & Exploit Profiling
--------------------------------------------------------

**Environment & Tools:** Kali Linux, ProjectDiscovery Nuclei, YAML

*   Deployed Nuclei against web-facing services to scan for known CVEs and authentication misconfigurations.
    
*   Wrote a custom jenkins-fuzz.yaml template to automate credential fuzzing against Jenkins login endpoints.
    
*   Configured compound matchers (HTTP 302, positive Location: header, negative loginError string) to confirm successful authentication bypass without false positives.
    

4\. Penetration Testing: Endpoint Exploitation & Domain Compromise
------------------------------------------------------------------

**Environment & Tools:** Metasploit (msfconsole), NetExec, Secretsdump, Evil-WinRM, VirtualBox

*   Used the ms17\_010 auxiliary scanner to identify unpatched SMBv1 hosts, then exploited EternalBlue to establish reverse shell sessions and dump local hashes.
    
*   Ran NetExec SMB user-hunting modules to locate Domain Administrator sessions across live hosts without triggering local defenses.
    
*   Moved laterally via Evil-WinRM, executing payloads in-memory through PowerShell Remoting to avoid touching disk and evade AV/EDR.
    
*   Ran a DCSync attack with Impacket secretsdump, replicating DC behavior over MS-DRSR to extract the full ntds.dit credential database.
    

5\. Network Security Monitoring & Real-Time Intrusion Detection
---------------------------------------------------------------

**Environment & Tools:** Ubuntu Linux, Snort (NIDS Mode)

*   Deployed and configured the Snort engine with a custom snort.conf across the lab network.
    
*   Wrote and tuned rules to detect ICMP sweeps, OS fingerprinting attempts, and app-layer attack signatures; validated alerts against live lab traffic.
    

6\. Applied Cryptography & Core Infrastructure Protocols
--------------------------------------------------------

**Environment & Tools:** dig, OpenPuff, Linux network utilities, SMTP

*   Compared MD5 vs SHA-256/512 outputs to demonstrate the avalanche effect and MD5's collision weakness for file integrity use cases.
    
*   Used dig +dnssec to pull and verify RRSIG/DNSKEY records, confirming DNSSEC chain-of-trust against cache poisoning scenarios.
    
*   Traced SMTP headers and MTA relay paths to identify spoofing anomalies and validate message routing integrity.
