# Phase One — SOC Operations and SIEM Foundations

Six-week foundation phase of the Cyberster Blue Team Internship. Covers building a SOC lab from the ground up,
deploying and tuning Wazuh SIEM, integrating Suricata IDS and pfSense firewall, threat intelligence and
vulnerability management, malware analysis, and a full capstone incident response investigation — each week
documented with a day-by-day breakdown and screenshot evidence.

**Instructor:** Abdullah Zia
**Intern:** Iqra Shahbaz
**Track:** Blue Team

## Weekly Breakdown

| Week | Days | Topic | Folder |
|---|---|---|---|
| 1 | 1–7 | SOC Foundations and Lab Setup | [Week 1](./Week-1-SOC-Foundations-and-Lab-Setup) |
| 2 | 8–14 | Detection, Custom Rules, and Log Analysis | [Week 2](./Week-2-Detection-Custom-Rules-and-Log-Analysis) |
| 3 | 15–21 | Suricata IDS Integration with Wazuh | [Week 3](./Week-3-Suricata-IDS-Integration-with-Wazuh) |
| 4 | 22–28 | pfSense Firewall and Advanced Monitoring | [Week 4](./Week-4-pfSense-Firewall-and-Advanced-Monitoring) |
| 5 | 29–35 | Malware Analysis and Incident Response | [Week 5](./Week-5-Malware-Analysis-and-Incident-Response) |
| 6 | — | Incident Response — Insider Threat Capstone | [Week 6](./Week-6-Incident-Response-Insider-Threat-Capstone) |

## What Was Built, Week by Week

**Week 1 — SOC Foundations and Lab Setup**
Built the lab environment from scratch: Oracle VirtualBox with a Wazuh OVA and Kali Linux OVA, dual-adapter
networking, and Wazuh agents deployed to both a Kali VM and a Windows 11 Pro host. Closed the week analysing
live alerts in the Wazuh dashboard.

**Week 2 — Detection, Custom Rules, and Log Analysis**
Turned the lab into an active detection environment: File Integrity Monitoring on both agents, three custom
Wazuh rules (new-user creation, SSH brute force, USB insertion), structured log analysis across Linux and
Windows sources, and an automated `firewall-drop` active response that successfully blocked a simulated
attacker.

**Week 3 — Suricata IDS Integration with Wazuh**
Added network-layer visibility with Suricata IDS, wrote three custom detection rules (Nmap scan, HTTP
traversal, ICMP flood), piped Suricata's alert stream into Wazuh, and correlated network-based and host-based
alerts in a single view. Closed with GeoIP-based firewall blocking for three countries.

**Week 4 — pfSense Firewall and Advanced Monitoring**
Introduced a dedicated firewall/perimeter (pfSense) in front of the lab, forwarded its logs into Wazuh,
integrated VirusTotal for hash-based threat intelligence, enabled MITRE ATT&CK mapping, and ran a full
vulnerability-management cycle — finding, prioritising, and patching a real CVE. Closed with a custom SOC
dashboard.

**Week 5 — Malware Analysis and Incident Response**
Downloaded and safely handled two real malware samples (Agent Tesla, Emotet) in an air-gapped VM. Ran static
analysis (file, exiftool, binwalk, strings) and interactive dynamic analysis (sandbox detonation), cross-checked
findings against VirusTotal, then engineered new Suricata and Wazuh detection rules directly from the IOCs
uncovered.

**Week 6 — Incident Response Capstone (Insider Threat)**
Investigated a full simulated insider-threat scenario end to end: data staging, Base64 encoding via
`certutil.exe`, HTTP exfiltration to an external listener, and an anti-forensics cleanup attempt. Reconstructed
the full attack timeline from FIM evidence, mapped four MITRE ATT&CK techniques, decoded the exfiltrated
payload, and closed the gap with a new custom detection rule — reported per the NIST SP 800-61 incident
response lifecycle.

## Progression Across the Phase
- **Weeks 1–2** — Built the lab environment and stood up core SIEM detection: FIM, custom rules, active response
- **Week 3** — Added network-layer visibility with Suricata IDS, correlated against host-based Wazuh alerts
- **Week 4** — Added perimeter defense (pfSense), threat intel enrichment (VirusTotal), and vulnerability management
- **Week 5** — Applied everything to real malware samples, from static/dynamic analysis to custom detection rules
- **Week 6** — Capstone: full incident response investigation end to end, following NIST SP 800-61

## Tools & Technologies Used
Wazuh SIEM · Suricata IDS · pfSense · VirtualBox · Wireshark · FIM/Syscheck · VirusTotal · Sandbox Analysis ·
exiftool · binwalk · strings · CyberChef · MITRE ATT&CK Framework · NIST SP 800-61

## Skills Demonstrated
- SOC lab environment design and deployment
- SIEM deployment, tuning, and custom detection-rule authoring
- Multi-tool alert correlation (IDS + SIEM + firewall)
- Threat intelligence integration and vulnerability management
- Static and dynamic malware analysis
- End-to-end incident response investigation and reporting
- MITRE ATT&CK technique mapping across every week
