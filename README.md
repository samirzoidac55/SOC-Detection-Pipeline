# SOC Detection Pipeline

A self-hosted SOC detection pipeline mapping real attack traffic to MITRE ATT&CK using Snort IDS + Wazuh SIEM, with automated email/PDF incident alerting.

(Verifying Sync)

## Tech Stack
![Snort 3](https://img.shields.io/badge/Snort-3-blue)
![Wazuh](https://img.shields.io/badge/Wazuh-SIEM-brightgreen)
![MITRE ATT&CK](https://img.shields.io/badge/MITRE-ATT&CK-red)
![Ubuntu](https://img.shields.io/badge/Ubuntu-Server%2FDesktop-orange)
![Postfix](https://img.shields.io/badge/Postfix-Alerting-yellow)

## Architecture Overview
The lab consists of three virtual machines running on a VirtualBox host-only network (`192.168.56.x`):
- **SOC Server (192.168.56.101):** Runs Snort IDS, Wazuh Manager, and Postfix for alert relay.
- **Kali Attacker (192.168.56.102):** Used for generating controlled attack traffic.
- **Victim (192.168.56.103):** An Ubuntu machine running the Wazuh Agent.

## How it Works
1. Attack traffic is generated from the Kali machine.
2. The Snort IDS detects the traffic based on custom rules and writes an alert to `alert_fast.txt`.
3. The Wazuh Manager decodes the alert via `snort3-alert-fast`.
4. The alert matches base rule `100100`, and child rules append relevant MITRE ATT&CK tags.
5. If the alert level is >= 12, Postfix triggers an email containing a PDF incident report.

## MITRE ATT&CK Coverage

| Rule ID | Snort SID | Detection | MITRE Technique | Tactic | Status |
| :--- | :--- | :--- | :--- | :--- | :--- |
| 100101 | 1000001 | ICMP Ping | T1046 | Discovery | Validated |
| 100102 | 1000003 | TCP Scan | T1046 | Discovery | Validated |
| 100103 | 1000002 | SSH Connection Attempt | T1021.004 | Lateral Movement | Validated |

## Setup Instructions
TODO: Add detailed installation and configuration steps.

## Known Issues / Lessons Learned
- Tuned out `arp_spoof` and `port_scan` false positives from Snort's built-in inspectors to reduce noise.
- Discovered and noted a packet-truncation warning ("IPv4 datagram length > captured length") affecting content-based rule matching.
- Removed the SQL injection rule; it requires a functional vulnerable web application for meaningful testing, which is out of scope for a simple `curl` request.

## Roadmap / Future Work (NOT YET BUILT)
- MITRE T1110 Brute Force detection (SSH)
- Wazuh Active Response for automated IP blocking (SOAR-lite)
- Wazuh File Integrity Monitoring for persistence/defense evasion detection (T1053, T1098, T1070)
- TheHive + Cortex for incident case management
- Azure cloud migration

## Screenshots
![Network Architecture](screenshots/00_architecture.png)
![ICMP Attack](screenshots/01_icmp_attack.png)
![TCP Scan Attack](screenshots/02_tcp_scan_attack.png)
![SSH Attack](screenshots/03_ssh_attack.png)
![Snort Logs](screenshots/04_snort_logs.png)
![Wazuh Alerts](screenshots/05_wazuh_alerts.png)
![Email Alert](screenshots/06_email_alert.png)
![PDF Report](screenshots/07_pdf_report.png)
 
