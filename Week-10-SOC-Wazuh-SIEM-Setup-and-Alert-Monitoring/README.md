# Week 10 – SOC: Wazuh SIEM Setup & Alert Monitoring

**Internship:** DG Interns Hub – Cybersecurity Internship  
**Project:** SOC – Wazuh SIEM Setup & Alert Monitoring  
**Prepared by:** SAMYUKTHA S.

## 1. Project Overview

This project focuses on deploying and exploring Wazuh as a Security Information and Event Management (SIEM) platform. It covers endpoint monitoring, Windows security events, File Integrity Monitoring (FIM), alert analysis, SOC incident investigation, and the relationship between Wazuh and Snort.

## 2. Lab Environment

| Component | Configuration |
|---|---|
| Wazuh version | 4.14.10 |
| Manager | Ubuntu Server – `soc-server` |
| Dashboard | Wazuh Dashboard |
| Monitored endpoint | Windows – `Windows-Endpoint` |
| Agent ID | 001 |
| Agent status | Active |
| FIM test source | Ubuntu Manager – agent 000 |

## 3. Project Structure

- `01-Wazuh-Fundamentals/` – Wazuh concepts, components, and architecture.
- `02-Wazuh-Installation/` – Installation and service verification evidence.
- `03-Wazuh-Agent-Deployment/` – Windows agent installation and connection evidence.
- `04-Security-Event-Monitoring/` – Windows security events and FIM testing.
- `05-Alert-Analysis/` – Analysis of ten observed alert records/categories and detailed investigation.
- `06-Wazuh-and-Snort/` – Snort evidence, Wazuh evidence, and architecture.
- `07-SOC-Incident-Investigation/` – Incident evidence and investigation report.
- `08-SOC-Dashboard/` – Dashboard screenshots and summary.
- `09-Final-Documentation/` – Final report and presentation.

## 4. Key Practical Activities

- Installed and verified Wazuh Manager, Indexer, and Dashboard.
- Deployed a Windows endpoint agent and verified its active connection.
- Generated controlled Windows account lifecycle events.
- Configured and tested File Integrity Monitoring.
- Reviewed ten observed alert records/categories.
- Investigated registry deletion alerts associated with an older Google Updater version.
- Reviewed Snort ICMP and HTTP detection evidence from the previous lab.
- Documented the separate Snort and Wazuh monitoring pipelines.
- Prepared a SOC incident investigation and dashboard summary.

## 5. Important Technical Notes

- Windows Security Event IDs and Wazuh rule IDs are different identifiers.
- Windows endpoint events belong to agent `001`.
- Ubuntu FIM events belong to agent `000`.
- The Google Updater registry deletion finding was assessed as likely routine updater cleanup; the exact cause was not verified.
- No confirmed malicious activity was established during that investigation.
- Direct Snort-to-Wazuh alert forwarding was not verified. The two monitoring pipelines are documented separately.
- Unsuccessful tests and evidence limitations are reported honestly.

## 6. Final Deliverables

- Wazuh fundamentals notes.
- Installation and agent deployment evidence.
- Security event monitoring and FIM evidence.
- Analysis of at least ten observed alert records/categories.
- Detailed alert investigation.
- SOC incident investigation.
- Wazuh and Snort architecture documentation.
- SOC dashboard summary.
- Final PDF report.
- Final PowerPoint presentation.

## 7. Conclusion

This project provided practical exposure to SIEM deployment, endpoint monitoring, security event analysis, File Integrity Monitoring, alert investigation, and SOC reporting using Wazuh. It also demonstrated how Snort and Wazuh can provide complementary security monitoring capabilities through separate pipelines.

**Project Status:** Practical activities and documentation completed; final repository verification and submission pending.