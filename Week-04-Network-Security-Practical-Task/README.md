# 🔐 DG Interns Hub — Week 04 Network Security Practical Task

![Internship](https://img.shields.io/badge/DG%20Interns%20Hub-Cybersecurity%20Internship-0A0A0A?style=for-the-badge)
![Week](https://img.shields.io/badge/Week-04%20Network%20Security-007BFF?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-2EA44F?style=for-the-badge)

![Kali Linux](https://img.shields.io/badge/Kali-Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white)
![Ubuntu](https://img.shields.io/badge/Ubuntu-Server-E95420?style=flat-square&logo=ubuntu&logoColor=white)
![Nmap](https://img.shields.io/badge/Nmap-Network%20Scanning-4682B4?style=flat-square)
![Wireshark](https://img.shields.io/badge/Wireshark-Traffic%20Analysis-1679A7?style=flat-square&logo=wireshark&logoColor=white)
![VMware](https://img.shields.io/badge/VMware-Virtual%20Lab-607078?style=flat-square&logo=vmware&logoColor=white)
![Apache](https://img.shields.io/badge/Apache-Web%20Server-D22128?style=flat-square&logo=apache&logoColor=white)

## Week 4: Network Security Practical Task

**Virtual Network Configuration, Service Exposure & Traffic Investigation**

---

## Intern Information

| Field | Details |
|---|---|
| Internship Program | DG Interns Hub — Cybersecurity Internship |
| Week | 04 |
| Practical Focus | Network Security |
| Participant | SAMYUKTHA S |
| Internship ID | DG/SEPTEMBER/CYBER/102 |

---

## 📌 Project Overview

This repository documents my Week 4 Network Security Practical Task completed as part of the DG Interns Hub Cybersecurity Internship.

The practical focused on building an authorized virtual cybersecurity laboratory and conducting an initial network security assessment.

The workflow combined virtual network configuration, web server deployment, service exposure analysis using Nmap, packet-level investigation using Wireshark, and final security validation.

All activities were performed in an isolated VMware laboratory using self-controlled Kali Linux and Ubuntu virtual machines.

## 🎯 Objectives

The main objectives of this practical were to:

- Configure an isolated virtual network using VMware Workstation.
- Establish connectivity between Kali Linux and Ubuntu Server.
- Configure and verify an Apache web server.
- Understand how service availability affects network port states.
- Perform controlled Nmap port scanning and service/version detection.
- Capture and investigate network traffic using Wireshark.
- Analyze ICMP, DNS and HTTP communication.
- Correlate service configuration, scan results and packet-level evidence.
- Complete an integrated network security assessment.
- Understand service exposure and its relationship to attack surface.

---

## 🧪 Lab Environment

The practical was performed using VMware Workstation with separate Host-only and NAT network interfaces.

### Virtual Machines

| System | Role | Interface | IP Address |
|---|---|---|---|
| Kali Linux | Security analysis / scanning machine | `eth0` — Host-only | `192.168.162.128/24` |
| Kali Linux | Internet / DNS access | `eth1` — NAT | `192.168.127.131/24` |
| Ubuntu Server | Target / Web server | `ens37` — Host-only | `192.168.162.131/24` |
| Ubuntu Server | Internet / package access | `ens33` — NAT | `192.168.127.130/24` |

### Network Configuration

| Network | Configuration | Purpose |
|---|---|---|
| VMnet1 | `192.168.162.0/24` | Isolated Host-only laboratory network |
| NAT | `192.168.127.0/24` | Internet, DNS and package access |

The Host-only network was used for communication and security testing between the virtual machines. NAT connectivity was used separately when Internet or DNS access was required.

### Lab Architecture

```text
                 VMware Workstation
                         |
              Virtual Network Interfaces
                         |
          ┌──────────────┴──────────────┐
          │                             │
     Host-only VMnet1                NAT Network
     192.168.162.0/24              192.168.127.0/24
          │                             │
    ┌─────┴─────┐                 ┌─────┴─────┐
    │           │                 │           │
 Kali Linux  Ubuntu Server     Kali Linux  Ubuntu Server
    │           │                 │           │
 .162.128   .162.131           .127.131   .127.130
    │           │
    └─────┬─────┘
          │
  Network Security Testing
          │
  ┌───────┴────────┐
  │                │
 Nmap          Wireshark
  │                │
 Port and       Packet-level
 Service        Traffic
 Discovery      Investigation
```

---

## 🛠️ Tools & Technologies Used

| Tool | Purpose |
|---|---|
| VMware Workstation | Virtualization and network isolation |
| Kali Linux | Security testing and network analysis |
| Ubuntu Server | Authorized target and web server |
| Nmap | Port scanning and service/version detection |
| Wireshark | Packet capture and traffic investigation |
| Apache | Web server configuration |
| curl | HTTP connectivity and response validation |
| UFW | Ubuntu firewall configuration |
| systemctl | Service management and verification |
| ss | Listening-port and socket inspection |

---

## 🔍 Task 1 — Basic Network Setup

Configured Kali Linux and Ubuntu Server on the VMware VMnet1 Host-only network.

### Activities Performed

- Configured the Host-only network interfaces.
- Verified IP addressing and routing.
- Established communication between Kali and Ubuntu.
- Tested bidirectional connectivity.
- Verified successful connectivity with `0%` packet loss in the connectivity tests.

### Lab Network Details

| System | Lab IP Address |
|---|---|
| Kali Linux | `192.168.162.128` |
| Ubuntu Server | `192.168.162.131` |

**Observation:**

Both virtual machines communicated successfully through the Host-only network.

**Evidence:**

`01-Network-Setup/`

---

## 🌐 Task 2 — Web Server Configuration

Configured Apache on the Ubuntu target to understand web service deployment and network exposure.

### Activities Performed

- Installed Apache on Ubuntu Server.
- Verified that the Apache service was active.
- Checked that Apache was listening on TCP port `80`.
- Configured UFW to allow TCP port `80`.
- Accessed the Apache web page successfully from Kali Linux.

### Service Validation

| Component | Observation |
|---|---|
| Web server | Apache |
| Service state | Active |
| Protocol | HTTP |
| Listening port | `TCP/80` |
| Firewall configuration | TCP/80 allowed |
| Remote access | Successful from Kali |

**Observation:**

The Apache service became accessible from the Kali machine after configuration and firewall adjustment.

**Evidence:**

`02-Web-Server/`

---

## 🔎 Task 3 — Nmap Network Scanning

Performed a controlled before-and-after scanning experiment to understand how service availability affects the network's observable port states.

### 3.1 Apache Service Stopped

With Apache stopped, the observed results were:

| Port | State | Service |
|---|---|---|
| `22/tcp` | Open | SSH |
| `80/tcp` | Closed | HTTP |

### 3.2 Apache Service Started

After starting Apache, the observed results changed:

| Port | State | Service |
|---|---|---|
| `22/tcp` | Open | SSH |
| `80/tcp` | Open | HTTP |

### 3.3 Service & Version Detection

Nmap service/version detection identified the following services:

| Port | Service | Detected Version |
|---|---|---|
| `22/tcp` | OpenSSH | `10.2p1 Ubuntu 2ubuntu3.5` |
| `80/tcp` | Apache httpd | `2.4.66 (Ubuntu)` |

### Key Observation

Starting the Apache service changed TCP port `80` from `closed` to `open`, while SSH on TCP port `22` remained open.

This demonstrated the relationship between service availability and the network's observable attack surface.

**Evidence:**

`03-Nmap/`

---

## 📡 Task 4 — Wireshark Traffic Analysis

Wireshark was used to capture and analyze network communication generated during the laboratory activities.

### Traffic Investigated

- ICMP Echo Request
- ICMP Echo Reply
- DNS Query
- DNS Response
- HTTP GET Request
- HTTP `200 OK` Response

### 4.1 ICMP Traffic

Captured and examined ICMP Echo Request and Echo Reply packets exchanged during connectivity testing.

**Purpose:** Understand basic network reachability and request-response communication.

### 4.2 DNS Traffic

Captured DNS queries and responses generated during the DNS experiment.

**Observation:** DNS troubleshooting demonstrated that the initial resolver on the Host-only network was not responding. Temporary NAT connectivity provided a working resolver for the DNS experiment.

### 4.3 HTTP Traffic

Analyzed HTTP communication between Kali Linux and the Ubuntu Apache web server.

The capture showed:

**HTTP GET Request:**

A request from Kali to:

`192.168.162.131:80`

**HTTP Response:**

```http
HTTP/1.1 200 OK
```

The response was returned by the Apache web server.

### 4.4 Protocol-Level Investigation

Packet analysis included:

| Layer / Protocol | Investigation |
|---|---|
| Ethernet | Frame-level communication |
| IPv4 | Source and destination addresses |
| TCP | Connection and communication flow |
| UDP | Datagram-based communication |
| ICMP | Echo requests and replies |
| DNS | Queries and responses |
| HTTP | GET requests and server responses |

**Key Observation:**

Wireshark provided packet-level evidence of communication between the virtual machines and helped validate the network activities performed during the practical.

**Evidence:**

`04-Wireshark/`

---

## 🔗 Task 5 — Integrated Network Security Mini Project

The final mini project combined the activities completed throughout the practical into one assessment workflow.

### Assessment Workflow

```text
Network Setup
     |
     ▼
Service Configuration
     |
     ▼
Nmap Discovery
     |
     ▼
Wireshark Traffic Analysis
     |
     ▼
Initial Service Validation
     |
     ▼
Final Nmap Assessment
     |
     ▼
HTTP Validation
     |
     ▼
Final Observations
```

### Integrated Activities

- Established connectivity between Kali and Ubuntu.
- Configured Apache on the Ubuntu target.
- Verified the web service and firewall configuration.
- Performed Nmap scans before and after Apache activation.
- Investigated ICMP, DNS and HTTP traffic using Wireshark.
- Correlated port-state changes with service configuration.
- Verified successful HTTP communication.

**Evidence:**

`05-Mini-Project/`

---

## 📊 Key Findings & Observations

The practical produced the following observations:

| Area | Finding |
|---|---|
| Network connectivity | Kali and Ubuntu communicated successfully through VMnet1 |
| Packet loss | `0%` packet loss observed during connectivity tests |
| Apache service | Service became accessible after configuration |
| TCP/80 before Apache startup | Closed |
| TCP/80 after Apache startup | Open |
| SSH service | TCP/22 remained open |
| Service detection | Nmap identified OpenSSH and Apache versions |
| ICMP analysis | Echo Request and Echo Reply traffic observed |
| DNS analysis | Query and response traffic captured using working resolver connectivity |
| HTTP analysis | GET request and `HTTP/1.1 200 OK` response observed |

### Important DNS Observation

The initial DNS resolver on the Host-only network did not respond during the experiment. Temporary NAT connectivity was used to obtain a working resolver for DNS traffic generation and capture.

This was a connectivity and configuration troubleshooting observation, not a confirmed DNS vulnerability.

---

## 🛡️ Security Analysis

The assessment followed an evidence-based interpretation approach:

**Observation → Exposure → Potential Risk → Confirmed Vulnerability**

The following distinctions were maintained:

- An open port indicates an accessible service, not automatically a vulnerability.
- Service/version detection provides information about exposed software and its configuration.
- Service exposure should be evaluated in the context of operational requirements.
- Firewall rules should restrict access to services that are not required.
- Packet captures provide additional context for validating network communication.

The practical demonstrated how unnecessary or broadly exposed services can increase the observable attack surface and why firewall configuration should be considered alongside service configuration.

No confirmed vulnerability was claimed solely from the observed open ports or service versions.

---

## 📁 Repository Structure

```text
Week-04-Network-Security-Practical-Task/
│
├── README.md
│
├── 01-Network-Setup/
│
├── 02-Web-Server/
│
├── 03-Nmap/
│
├── 04-Wireshark/
│
├── 05-Mini-Project/
│
├── 06-Report/
│
├── 07-Presentation/
│
└── 08-Network-Topology/
```

The folders contain practical screenshots, supporting documentation, report materials, presentation slides and network topology evidence.

---

## 📄 Project Deliverables

### Practical Evidence

Screenshots documenting the network configuration, Apache deployment, Nmap scanning, Wireshark packet analysis and integrated mini project.

### Technical Report

A 10–12 page technical report covering the practical workflow, configurations, observations, findings and security analysis.

### Presentation

A 5–8 slide presentation summarizing the project activities and results.

### Network Topology

An advanced visual representation of the virtual laboratory network.

---

## 🧠 Learning Outcomes

This practical strengthened my understanding of:

- Virtual networking and VM isolation.
- IP addressing, subnets and routing.
- Service configuration and exposure.
- Nmap port and service discovery.
- Wireshark packet-level analysis.
- ICMP, DNS, TCP and HTTP communication.
- HTTP request and response analysis.
- Cross-tool evidence correlation.
- Evidence-based security assessment.
- Basic network troubleshooting and defensive hardening.

---

## 🔒 Scope & Safety

All scanning, traffic analysis and testing were performed only against self-controlled virtual machines in an authorized laboratory environment.

The practical focused on:

- Virtual network configuration.
- Service deployment and validation.
- Network security assessment.
- Packet-level traffic investigation.
- Defensive security understanding.

No third-party systems, credentials or real-world traffic were targeted or intercepted.

---

## 📚 References

- [Nmap Documentation](https://nmap.org/book/man.html)
- [Wireshark Documentation](https://www.wireshark.org/docs/)
- [Ubuntu Server Documentation](https://documentation.ubuntu.com/server/)
- [Apache HTTP Server Documentation](https://httpd.apache.org/docs/)
- [VMware Documentation](https://docs.vmware.com/)

---

## 🎓 Internship Information

| Field | Details |
|---|---|
| Program | DG Interns Hub — Cybersecurity Internship |
| Week | 04 |
| Focus | Network Security Practical Task |
| Participant | SAMYUKTHA S |
| Internship ID | DG/SEPTEMBER/CYBER/102 |

---

## 🏁 Conclusion

The Week 04 Network Security Practical provided hands-on experience in configuring and assessing a virtual network environment.

The project progressed from virtual network setup and Apache deployment to Nmap service discovery, Wireshark packet investigation and integrated network validation.

One of the key observations was that starting the Apache service changed TCP port 80 from closed to open, demonstrating how service configuration directly affects network exposure.

The practical also reinforced the importance of combining network scanning with packet-level investigation. Nmap helped identify accessible services, while Wireshark provided supporting evidence of the communication taking place between the systems.

**DG Interns Hub — Cybersecurity Internship | Week 04**

*Understand the Network. Analyze the Traffic. Strengthen the Security.*
