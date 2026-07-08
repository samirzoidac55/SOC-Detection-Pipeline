# SOC Detection Pipeline

A self-hosted Security Operations Center (SOC) detection pipeline designed to map real attack traffic to the MITRE ATT&CK framework. This project utilizes Snort IDS for signature-based detection and Wazuh SIEM for log analysis and correlation, featuring automated incident response through email and PDF reporting.

## Key Features
- **Real-time Detection:** Utilizes Snort 3 for identifying malicious network activity based on custom rules.
- **Log Correlation & Analysis:** Wazuh Manager aggregates and decodes Snort alerts, mapping them to relevant MITRE ATT&CK techniques.
- **Automated Incident Response:** Automatically triggers email alerts with PDF incident reports for high-severity detections.
- **Controlled Lab Environment:** Architected to run on a VirtualBox host-only network, perfect for security research and training.

## Tech Stack
- **IDS:** Snort 3
- **SIEM:** Wazuh
- **Framework:** MITRE ATT&CK
- **Mail Relay:** Postfix
- **OS:** Ubuntu
