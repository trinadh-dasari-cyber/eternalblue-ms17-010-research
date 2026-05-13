# 💀 EternalBlue (MS17-010) Exploitation Research

**Controlled reproduction of CVE-2017-0144 — the SMB vulnerability behind the WannaCry ransomware outbreak**

> ⚠️ Disclaimer: This research was conducted in a fully isolated, controlled lab environment for academic and educational purposes only. No production systems were involved.

---

## Overview

This project reproduced the EternalBlue exploit (CVE-2017-0144, CVSS 9.3) in a sandboxed AWS EC2 environment. The goal was to deeply understand the vulnerability mechanics, capture and analyze the exploit traffic, and map the attack chain to MITRE ATT&CK — informing both offensive research and defensive hardening strategies.

---

## Lab Architecture

- **Cloud Platform:** AWS EC2
- **Attacker Machine:** Kali Linux
- **Target Machine:** Windows Server 2008 R2 (unpatched, SMBv1 enabled)
- **Network:** Isolated VPC, no internet egress from target

---

## What Was Done

### Exploit Reproduction
- Configured a vulnerable Windows Server 2008 R2 instance with SMBv1 enabled and MS17-010 unpatched
- Used Metasploit Framework to execute the exploit chain
- Achieved remote code execution and SYSTEM-level shell access

### Network Traffic Analysis
- Captured full packet capture using Wireshark during the exploit
- Analyzed SMB negotiation sequence, shellcode delivery, and RCE stages at the packet level
- Identified key indicators of compromise (IOCs) visible in network traffic

### MITRE ATT&CK Mapping

- **T1210** — Exploitation of Remote Services (Initial Access)
- **T1059** — Command and Scripting Interpreter (Execution)
- **T1055** — Process Injection (Defense Evasion / Privilege Escalation)

---

## Key Findings & Mitigations

- SMBv1 enabled by default on legacy systems → Disable via PowerShell or Group Policy
- MS17-010 patch not applied → Apply KB4012212 / KB4012215 immediately
- Lateral movement possible post-exploitation → Network segmentation + host-based firewall rules
- No detection of exploit traffic → Deploy SMB traffic monitoring in SIEM

---

## Academic Output

Delivered a 35-minute capstone presentation covering:
- Full exploit mechanics and root cause analysis
- Packet-level walkthrough of the attack chain
- Detection strategies and remediation recommendations

---

## Skills Demonstrated

`Metasploit` `Wireshark` `Kali Linux` `AWS EC2` `CVE Analysis` `CVSS Scoring` `MITRE ATT&CK` `SMB Protocol` `Vulnerability Research` `Network Forensics`
