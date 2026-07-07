# Demo Video Script: SOC Detection Pipeline (60-90s)

**[00:00-00:05] Context:**
Show the network architecture diagram on screen.
*Voiceover:* "This is a self-hosted SOC detection pipeline using Snort and Wazuh to map attack traffic directly to MITRE ATT&CK techniques."

**[00:05-00:25] Attack Generation:**
Show Kali terminal. Execute an `nmap` scan against the victim.
*Voiceover:* "I'll start by simulating a reconnaissance phase using Nmap against our victim machine."

**[00:25-00:40] Snort Detection:**
Cut to SOC Server terminal showing the Snort alert log updating.
*Voiceover:* "Immediately, Snort detects the TCP SYN scan and logs the event."

**[00:40-00:60] Wazuh Correlation:**
Cut to Wazuh Dashboard/Alert output showing the rule `100102` with the MITRE technique `T1046` Discovery.
*Voiceover:* "Wazuh ingests this alert, correlates it, and automatically tags it with the relevant MITRE ATT&CK Tactic and Technique."

**[00:60-00:80] Incident Alerting:**
Cut to the Gmail inbox showing a new alert email, then open the attached PDF report.
*Voiceover:* "Finally, the system triggers an incident alert, emailing a PDF report to the security team for immediate review."

**[00:80-00:90] Recap:**
Final shot showing the pipeline components.
*Voiceover:* "A complete, automated workflow from detection to incident reporting. Thanks for watching."
