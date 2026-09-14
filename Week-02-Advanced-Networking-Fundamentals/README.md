# DG Interns Hub — Cybersecurity Internship

![Internship](https://img.shields.io/badge/DG%20Interns%20Hub-Cybersecurity%20Internship-**0A0A0A**?style=for-the-badge) ![Week](https://img.shields.io/badge/Week%**2002**-Advanced%20Networking%20%26%20Security-**00BFFF**?style=for-the-badge) ![Status](https://img.shields.io/badge/Status-Completed-**2EA44F**?style=for-the-badge)

## Week 2: Advanced Networking, Analysis & Security Concepts

**Intern:** **SAMYUKTHA** S **Intern ID:** DG/**SEPTEMBER**/**CYBER**/**102**

---

## Overview

This repository contains my Week 2 work for the **DG Interns Hub Cybersecurity Internship**.

Week 2 focused on **Advanced Networking, Analysis & Security Concepts**, combining theoretical learning with practical network traffic analysis, basic network scanning, network configuration, and safe security concept simulations.

---

## Topics Covered

### Part 1 — Theory

- Port & Services
- Networking Devices
- Network Security Basics
- Man-in-the-Middle (**MITM**)
- Denial of Service (DoS)
- Packet Sniffing
- Basic Security Prevention Methods

### Part 2 — Practical

Practical activities were performed using:

- Wireshark
- Nmap
- Cisco Packet Tracer

---

## Wireshark — Packet Analysis

Used Wireshark to capture and analyze normal network traffic.

Activities included:

- Selecting the active Wi-Fi 2 interface
- Generating traffic by visiting `[https://google.com`](https://google.com`)
- Filtering **DNS** traffic
- Inspecting a **DNS** response
- Filtering **TLS** traffic
- Inspecting TLSv1.2 application-data traffic

Observed **DNS** communication using **UDP** port `53` and **TLS** communication associated with **HTTPS** traffic using port `**443**`.

---

## Nmap — Network Scanning

Performed basic network scanning and service/version detection against the authorized target:

`scanme.nmap.org`

Commands used:

```bash nmap -T4 scanme.nmap.org The scans were used to identify open ports, services, and service versions on the authorized target.

Observed services included **SSH** and **HTTP**, along with other ports reported by the scan. ```

---

## Packet Tracer — LAN Setup

Created a basic **LAN** using Cisco Packet Tracer.

Configuration:

Device	IP Address	Subnet Mask
**PC1**	   **192**.**168**.1.10	**255**.**255**.**255**.0
**PC2**	   **192**.**168**.1.11	**255**.**255**.**255**.0

Connectivity was tested using ping, with the practical evidence showing successful connectivity.

---

## Safe MITM Concept Simulation

Created a controlled Packet Tracer topology to understand the conceptual position of an attacker in a Man-in-the-Middle scenario.

Configuration:

Device	                IP Address
**PC1**-Victim	            **192**.**168**.1.10
**PC2**-Conceptual Attacker	**192**.**168**.1.20
Router	                **192**.**168**.1.1

The simulation was performed only as a safe conceptual exercise.

No real traffic interception, **ARP** poisoning, credential capture, password theft, or traffic manipulation was performed.

---

## Repository Structure

Week-02-Advanced-Networking-Fundamentals/
│
├── **README**.md
│
├── Part-1-Theory/
│   ├── **README**.md
│   └── Week 2.pdf
│
├── Part-2-Practical/
│   ├── **README**.md
│   └── Screenshots/
│       ├── Nmap/
│       ├── Packet-Tracer/
│       ├── Safe-**MITM**/
│       └── Wireshark/
│
└── Documentation/
    ├── **README**.md
    ├── DG_Interns_Hub_Week2_Presentation_Samyuktha_S_FINAL.pptx
    └── DG_Interns_Hub_Week2_Report_Samyuktha_S_FINAL.pdf

---

## Learning Outcome

This week helped me connect advanced networking and security concepts with practical activities.

Through Wireshark, I gained hands-on experience in analyzing **DNS** and **TLS** traffic.

Using Nmap, I practiced authorized network scanning and service/version detection.

Cisco Packet Tracer helped me understand **LAN** configuration and visualize a safe conceptual **MITM** scenario in a controlled environment.

---
