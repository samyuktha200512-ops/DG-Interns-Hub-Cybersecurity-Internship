# DG Interns Hub — Cybersecurity Internship

![Internship](https://img.shields.io/badge/DG%20Interns%20Hub-Cybersecurity%20Internship-0A0A0A?style=for-the-badge)
![Weeks](https://img.shields.io/badge/Weeks%2001%20%26%2002-Completed-00BFFF?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-2EA44F?style=for-the-badge)

---

## 👩‍💻 Intern Details

| Field | Details |
|---|---|
| **Intern** | SAMYUKTHA S |
| **Intern ID** | DG/SEPTEMBER/CYBER/102 |
| **Internship** | DG Interns Hub — Cybersecurity Internship |
| **Domain** | Cybersecurity |
| **Batch** | 3 |

---

# 📘 Week 1 — Networking Fundamentals

## Overview

Week 1 focused on **Networking Fundamentals**, combining theoretical concepts with practical network diagnostics and a Cisco Packet Tracer implementation.

---

## 📚 Part 1 — Theory

### Topics Covered

- OSI Model
- Encapsulation and Decapsulation
- TCP/IP Model
- OSI vs TCP/IP
- HTTP
- HTTPS
- FTP
- DNS
- DHCP
- IPv4 Addressing
- Public vs Private IP
- Static vs Dynamic IP
- Loopback
- Subnet Mask
- CIDR
- Basic Subnetting

---

## 🧪 Part 2 — Practical

The following network diagnostic commands were practiced:

```text
ping
ipconfig
ifconfig
tracert
traceroute
```

Practical observations were performed using:

- Windows
- Kali Linux

### Practical Work

The activities included observing network configuration, testing connectivity, resolving domain names, and examining network paths using diagnostic commands.

---

## 🌐 Cisco Packet Tracer

A basic network topology was implemented using:

```text
PC → 2960-24TT Switch → 2911 Router
```

### Configuration

| Device | Configuration |
|---|---|
| PC | `192.168.1.10` |
| Subnet Mask | `255.255.255.0` |
| Default Gateway | `192.168.1.1` |
| Router GigabitEthernet0/0 | `192.168.1.1` |

Connectivity was verified using a successful ping from the PC to the router.

---

## 🎯 Week 1 Learning Outcome

Week 1 helped me build a foundation in networking concepts and connect theoretical knowledge with practical network diagnostic commands and Cisco Packet Tracer configuration.

---

# 🔐 Week 2 — Advanced Networking, Analysis & Security Concepts

## Overview

Week 2 focused on **advanced networking concepts, network traffic analysis, basic scanning, networking devices, security concepts, and safe network simulations**.

---

## 📚 Tasks Completed

### 1. Port & Services

Studied common network ports and services and their role in network communication.

---

### 2. Networking Devices

Covered common networking devices and their functions within a network.

---

### 3. Network Security Basics

Studied fundamental network security concepts and common security threats.

---

### 4. Packet Analysis — Wireshark

Performed practical packet analysis using **Wireshark**.

Activities included:

- Capturing network traffic
- Observing DNS traffic
- Filtering DNS packets
- Observing TLS traffic
- Examining application data over HTTPS

### Wireshark Environment

The practical analysis was performed on the active Wi-Fi interface.

The captured traffic included DNS and TLS communication generated while accessing:

```text
https://google.com
```

---

### 5. Network Scanning — Nmap

Performed authorized network scanning using:

```bash
nmap -T4 scanme.nmap.org
nmap -sV -T4 scanme.nmap.org
```

The scans were performed against the authorized:

```text
scanme.nmap.org
```

### Observed Services

The scan identified services including:

| Port | Service / Observation |
|---|---|
| `22/tcp` | SSH |
| `80/tcp` | HTTP |
| `9929/tcp` | Nping echo |
| `31337/tcp` | Elite / tcpwrapped observation |

The service/version scan also identified information such as:

- OpenSSH
- Apache HTTP Server
- Linux host information

---

### 6. Packet Tracer LAN Setup

A simulated LAN was configured using Cisco Packet Tracer.

### IP Configuration

| Device | IP Address | Subnet Mask |
|---|---|---|
| PC1 | `192.168.1.10` | `255.255.255.0` |
| PC2 | `192.168.1.11` | `255.255.255.0` |

Connectivity was verified through the available ping test.

---

### 7. Safe MITM Concept Simulation

A **safe, conceptual MITM simulation** was created using Cisco Packet Tracer.

### Network Configuration

| Device | IP Address |
|---|---|
| PC1 — Victim | `192.168.1.10` |
| PC2 — Attacker | `192.168.1.20` |
| Router | `192.168.1.1` |

The activity was limited to understanding the network topology and communication path.

> **Safety Boundary:** No real traffic interception, ARP poisoning, credential capture, password theft, or traffic manipulation was performed.

Connectivity to the router was verified using a ping test.

---

## 🎯 Week 2 Learning Outcome

Week 2 extended my networking foundation into:

- Network traffic analysis
- DNS and TLS packet observation
- Authorized network scanning
- Service and version identification
- LAN configuration
- Network security concepts
- Safe conceptual MITM simulation

---

# 📂 Repository Structure

```text
DG-Interns-Hub-Cybersecurity-Internship/
│
├── README.md
│
├── Week-01-Networking-Fundamentals/
│   │
│   ├── README.md
│   │
│   ├── Part-1-Theory/
│   │   ├── README.md
│   │   ├── Networking-Commands-Practical.pdf
│   │   └── Networking-Fundamentals-Theory.pdf
│   │
│   ├── Part-2-Practical/
│   │   ├── README.md
│   │   └── Screenshots/
│   │       ├── Connecting.png
│   │       ├── ifconfig.png
│   │       ├── ipconfig.png
│   │       ├── pc-configuration.png
│   │       ├── ping-google.png
│   │       ├── ping-verification.png
│   │       ├── router-configuration.png
│   │       ├── Topology.png
│   │       ├── traceroute.png
│   │       └── tracert.png
│   │
│   ├── Cisco-Packet-Tracer/
│   │   ├── README.md
│   │   └── week-1-network.pkt
│   │
│   └── Documentation/
│       ├── README.md
│       ├── Final-Consolidated-PPT.pdf
│       └── Final-consolidated-report.pdf
│
└── Week-02-Advanced-Networking-Fundamentals/
    │
    ├── README.md
    │
    ├── Part-1-Theory/
    │   ├── README.md
    │   └── Week 2.pdf
    │
    ├── Part-2-Practical/
    │   ├── README.md
    │   └── Screenshots/
    │       ├── Nmap/
    │       ├── Packet-Tracer/
    │       ├── Safe-MITM/
    │       └── Wireshark/
    │
    └── Documentation/
        ├── README.md
        ├── DG_Interns_Hub_Week2_Presentation_Samyuktha_S_FINAL.pptx
        └── DG_Interns_Hub_Week2_Report_Samyuktha_S_FINAL.pdf
```

---

# 📊 Internship Progress

| Week | Assignment | Status |
|---|---|---|
| Week 1 | Networking Fundamentals | ✅ Completed |
| Week 2 | Advanced Networking, Analysis & Security Concepts | ✅ Completed |

---

# 🏆 Overall Learning Outcome

Through the first two weeks of the **DG Interns Hub Cybersecurity Internship**, I developed a foundation in networking and progressed into practical network analysis and security concepts.

### Week 1

Built fundamental knowledge of networking models, protocols, IP addressing, subnetting, network diagnostic commands, and Cisco Packet Tracer configuration.

### Week 2

Extended that foundation through Wireshark packet analysis, authorized Nmap scanning, service identification, LAN configuration, network security concepts, and a safe conceptual MITM simulation.

---

## 🛠️ Tools Used

### Week 1

- Windows Command Prompt
- Kali Linux
- Cisco Packet Tracer

### Week 2

- Wireshark
- Nmap
- Cisco Packet Tracer

---

## 📁 Documentation

The repository contains:

- Theory documentation
- Practical evidence
- Screenshots
- Cisco Packet Tracer work
- Week 1 report and presentation
- Week 2 report and presentation

All practical work documented in this repository is based on the activities performed during the respective internship weeks.

---

## 🔗 Repository

**DG Interns Hub — Cybersecurity Internship**

**Intern:** SAMYUKTHA S  
**Intern ID:** DG/SEPTEMBER/CYBER/102

---
```
