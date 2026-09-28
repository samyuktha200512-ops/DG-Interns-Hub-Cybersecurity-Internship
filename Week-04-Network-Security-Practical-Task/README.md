# Week 4 – Network Security Practical Task

## Overview

Week 4 focused on building an authorized virtual cybersecurity lab and performing an initial network security assessment. The practical workflow connected network setup, service configuration, Nmap scanning, Wireshark traffic analysis, and final validation.

## Objective

Understand basic network setup and perform initial security testing in an isolated, authorized lab environment.

## Lab Environment

### Virtualization
- VMware Workstation

### Kali Linux – Attacker / Security Analyst
- `eth0` → Host-only / VMnet1
- Lab IP: `192.168.162.128/24`
- `eth1` → NAT
- NAT IP: `192.168.127.131/24`

### Ubuntu – Target / Web Server
- `ens37` → Host-only / VMnet1
- Lab IP: `192.168.162.131/24`
- `ens33` → NAT
- NAT IP: `192.168.127.130/24`

### Networks
- VMnet1 Host-only lab network: `192.168.162.0/24`
- NAT: used separately for Internet, DNS and package access

## Tools Used

- VMware Workstation
- Kali Linux
- Ubuntu Server
- Nmap
- Wireshark
- curl
- UFW
- systemctl
- ss

## Tasks Completed

### Task 1 – Basic Network Setup
- Configured Kali and Ubuntu on the VMnet1 Host-only network.
- Verified IP addressing and routing.
- Verified bidirectional connectivity between Kali and Ubuntu.
- Observed `0%` packet loss in connectivity tests.

### Task 2 – Web Server Configuration
- Installed Apache on the Ubuntu target.
- Verified that the Apache service was active.
- Verified that Apache was listening on TCP port `80`.
- Updated UFW to allow TCP/80.
- Successfully accessed the Apache page from Kali.

### Task 3 – Nmap Network Scanning
A controlled before/after experiment was performed.

With Apache stopped:
- `22/tcp` → open / SSH
- `80/tcp` → closed / HTTP

With Apache started:
- `22/tcp` → open / SSH
- `80/tcp` → open / HTTP

Service/version detection identified:
- OpenSSH `10.2p1 Ubuntu 2ubuntu3.5`
- Apache httpd `2.4.66` (Ubuntu)

### Task 4 – Wireshark Traffic Analysis
Captured and analyzed:
- ICMP Echo Request / Echo Reply
- DNS Query / DNS Response
- HTTP GET Request
- HTTP `200 OK` Response

Packet analysis included:
- Ethernet
- IPv4
- TCP/UDP
- ICMP
- DNS
- HTTP
- Source/destination addresses and ports
- TCP communication flow

### Task 5 – Mini Project
Integrated the complete workflow:

```text
Network Setup
    ↓
Service Configuration
    ↓
Nmap Discovery
    ↓
Wireshark Traffic Analysis
    ↓
Final Service Validation
    ↓
Final Nmap Assessment
    ↓
HTTP Validation
```

## Key Findings

- Kali and Ubuntu communicated successfully through the VMnet1 lab network.
- Starting Apache changed TCP/80 from `closed` to `open`.
- Nmap service/version detection identified the exposed SSH and HTTP services.
- Wireshark provided packet-level evidence for ICMP, DNS and HTTP communication.
- HTTP analysis showed a request from Kali to `192.168.162.131:80` and an `HTTP/1.1 200 OK` response from Apache.
- DNS troubleshooting demonstrated that the initial resolver on the Host-only network was not responding; temporary NAT connectivity provided a working resolver for the DNS experiment.

## Security Analysis

The assessment distinguishes between:

**Observation → Exposure → Potential Risk → Confirmed Vulnerability**

An open port or detected service was treated as an exposure/observation and was **not automatically classified as a confirmed vulnerability** without supporting evidence.

The practical also demonstrated how unnecessary or broadly exposed services can increase the observable attack surface and why firewall configuration should be considered alongside service configuration.

## Evidence

The repository contains genuine screenshots collected from the authorized lab environment.

```text
01-Network-Setup/
02-Web-Server/
03-Nmap/
04-Wireshark/
05-Mini-Project/
08-Network-Topology/
```

The report and presentation are stored under:

```text
06-Report/
07-Presentation/
```

## Learning Outcomes

This week strengthened practical understanding of:

- Virtual networking and VM isolation
- IP addressing, subnets and routing
- Service exposure and attack surface
- Nmap port and service discovery
- Wireshark packet-level analysis
- ICMP, DNS, TCP and HTTP behavior
- Cross-tool correlation
- Evidence-based security assessment
- Basic troubleshooting and defensive hardening

## Safety and Scope

All scanning, traffic analysis and testing were performed only against self-controlled virtual machines in an authorized laboratory environment.

No third-party systems, credentials or real-world traffic were targeted or intercepted.

## Deliverables

- Week 4 practical evidence
- 10–12 page technical report (PDF)
- 5–8 slide presentation (PPT)
- Advanced network topology
- Nmap and Wireshark evidence

---

**DG Interns Hub – Cybersecurity Internship**  
**Week 4 – Network Security Practical Task**
