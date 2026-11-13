# Week 10 – Folder 06: Wazuh and Snort

DG Interns Hub – Cybersecurity Internship | SOC – Wazuh SIEM Setup & Alert Monitoring
Intern: Samyuktha S. | Internship ID: DG/SEPTEMBER/CYBER/102

## Contents

| Item | Description |
|---|---|
| `Week-10-Folder-06-Wazuh-and-Snort.pdf` | Report section (7 pages, 16 numbered figures): introduction, Snort monitoring, Wazuh monitoring, Wazuh vs Snort, combined architecture, integration status, analyst workflow, conclusion. |
| `01-Snort-Evidence/` | Seven original Week 09 screenshots, reused unchanged. |
| `02-Wazuh-Evidence/` | Nine original Week 10 screenshots, reused unchanged. |
| `03-Architecture/Wazuh-Snort-SOC-Architecture.png` | Diagram of two separate pipelines (network: Snort; endpoint: Wazuh) joined only by the analyst's manual correlation. |

Figures in the PDF are cropped copies for readability. The files in the evidence folders are the unmodified originals.

## Evidence index

### 01-Snort-Evidence (Week 09)

| File | What it visibly shows | Report figure |
|---|---|---|
| `01-Snort-Installation.png` | Snort 2.9.20 package setup; default interface ens33 | Figure 1 |
| `02-Version-Verification.png` | `snort -V`: Snort 2.9.20 GRE (Build 82) | Figure 2 |
| `03-Test-Mode.png` | "Snort successfully validated the configuration!" | Figure 3 |
| `02-ICMP-Ping-Detection.png` | `local.rules` containing **only the ICMP rule** (rule text, not alert output) | Mentioned in Section B.3 |
| `03-HTTP-Traffic-Detection.png` | `local.rules` containing the ICMP rule (sid 1000001) and HTTP rule (sid 1000002) (rule text, not alert output) | Figure 4 |
| `01-Ping-Test.png` | Snort console alerts for sid 1000001 plus built-in rules 527 and 1917 | Figure 5 |
| `02-HTTP-Test.png` | HTTP page content in the terminal; **no Snort alert is visible** | Figure 6 |

### 02-Wazuh-Evidence (Week 10)

| File | What it visibly shows | Report figure |
|---|---|---|
| `01-Wazuh-Installation-Completed.png` | Indexer cluster GREEN, dashboard initialised, "Installation finished" | Figure 7 |
| `02-Wazuh-Services-Status.png` | wazuh-indexer and wazuh-dashboard active (running) | Figure 8 |
| `03-Wazuh-Dashboard-Overview.png` | Dashboard overview captured **before** an agent was registered | Figure 9 |
| `01-Wazuh-Windows-Agent-Service-Running.png` | Agent install command (manager 192.168.38.128, name Windows-Endpoint); WazuhSvc Running | Figure 10 |
| `01-Wazuh-Agent-Active-Connection.png` | `agent_control -l`: server (000) and Windows-Endpoint (001) active | Figure 11 |
| `02-Wazuh-Agent-Dashboard-Status.png` | Endpoints view: 1 active agent, Windows 11 Home, v4.14.10 | Figure 12 |
| `03-Wazuh-Detected-User-Creation-Event.png` | Threat Hunting query for Windows event 4720: 1 event | Figure 13 |
| `07-Wazuh-Detected-Account-Deleted-Alert.png` | Raw alert for event 4726, rule 60111, level 8 | Figure 14 |
| `02-FIM-File-Modification-Alert.png` | Syscheck alerts 554 and 550 on soc-server (agent 000) | Figure 15 |

## Integration status and limitations

- Snort (Week 09) and Wazuh (Week 10) were configured and tested **separately**.
- Direct forwarding of Snort alerts into Wazuh was **not verified**. No supplied evidence shows Wazuh collecting Snort alerts, so the architecture diagram shows two separate pipelines.
- No supplied screenshot shows a Snort "HTTP Traffic Detected" (sid 1000002) alert. The Week 09 findings note records HTTP alerts, but the report treats this as not independently evidenced.
- Snort was used as a passive IDS; no inline blocking was tested.
- Rule 60109 (account created) and its level come from the Folder 05 alert analysis, not from a screenshot in this folder.
- The ten-alert analysis and the registry-deletion investigation are in Folder 05 and are not repeated here.

## Placement

Place this folder inside the Week 10 project folder, next to `01-Wazuh-Fundamentals` to `05-Alert-Analysis`:

```
Week-10-SOC-Wazuh-SIEM-Setup-and-Alert-Monitoring/
├── 01-Wazuh-Fundamentals/
├── 02-Wazuh-Installation/
├── 03-Wazuh-Agent-Deployment/
├── 04-Security-Event-Monitoring/
├── 05-Alert-Analysis/
└── 06-Wazuh-and-Snort/        <- this folder
```
