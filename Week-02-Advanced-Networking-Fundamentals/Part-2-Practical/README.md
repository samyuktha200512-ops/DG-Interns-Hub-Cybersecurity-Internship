# Week 2 — Part 2: Practical

![Internship](https://img.shields.io/badge/DG%20Interns%20Hub-Cybersecurity%20Internship-**0A0A0A**?style=for-the-badge) ![Part](https://img.shields.io/badge/Part%**202**-Practical-**00BFFF**?style=for-the-badge) ![Week](https://img.shields.io/badge/Week%**2002**-Advanced%20Networking%20%26%20Security-**00BFFF**?style=for-the-badge)

## Part 2: Practical Work

**Intern:** **SAMYUKTHA** S **Intern ID:** DG/**SEPTEMBER**/**CYBER**/**102**

---

## Overview

This folder contains the **practical work and original screenshots** completed for Week 2 of the **DG Interns Hub Cybersecurity Internship**.

The practical activities covered packet analysis, network scanning, **LAN** configuration, and a safe conceptual **MITM** simulation.

---

## Tools Used

- **Wireshark** — Packet capture and traffic analysis
- **Nmap** — Network scanning and service/version detection
- **Cisco Packet Tracer** — **LAN** configuration and safe network security simulation

---

## 1. Wireshark — Packet Analysis

Wireshark was used to capture and analyze normal network traffic.

### Activities Performed

- Selected the active Wi-Fi 2 interface
- Started packet capture
- Visited `[https://google.com`](https://google.com`)
- Applied the `dns` display filter
- Inspected **DNS** traffic and a **DNS** response
- Applied the `tls` display filter
- Inspected TLSv1.2 application-data traffic

### Observations

The captured traffic included **DNS** communication using **UDP** port `53` and **TLS** communication associated with **HTTPS** traffic using port `**443**`.

### Evidence

Original screenshots are available in:

`Screenshots/Wireshark/`

---

## 2. Nmap — Network Scanning

Nmap was used for basic network scanning and service/version detection against the authorized target:

`scanme.nmap.org`

### Commands Used

```bash nmap -T4 scanme.nmap.org nmap -sV -T4 scanme.nmap.org Observations

The scan identified open and filtered ports on the authorized target.

Observed services included:

**SSH** **HTTP** ### Nping Echo Elite

Service/version detection also identified:

OpenSSH 6.6.1p1 Apache httpd 2.4.7

The -T4 option was used because the default scan took an unusually long time in the working environment due to repeated retransmissions.

Evidence

Original screenshots are available in:

Screenshots/Nmap/

## Packet Tracer — LAN Setup

A basic **LAN** was created using Cisco Packet Tracer.

Configuration
Device	IP Address	Subnet Mask
**PC1**	**192**.**168**.1.10	**255**.**255**.**255**.0
**PC2**	**192**.**168**.1.11	**255**.**255**.**255**.0

A connectivity test was performed using ping.

The practical evidence shows a successful ping with:

4 packets received 0% packet loss Evidence

Original screenshots are available in:

Screenshots/Packet-Tracer/

## Safe MITM Concept Simulation

A controlled Packet Tracer topology was created to understand the conceptual position of an attacker in a Man-in-the-Middle scenario.

Configuration
Device	Role	IP Address
**PC1**	Victim	**192**.**168**.1.10
**PC2**	Conceptual Attacker	**192**.**168**.1.20
Router	Gateway	**192**.**168**.1.1

Connectivity between **PC1** and the router was tested using ping.

The test showed:

4 replies received 0% packet loss ### Safety Boundary

This was a safe and conceptual simulation only.

The activity did not involve:

Real traffic interception **ARP** poisoning Credential capture Password theft Traffic manipulation Evidence

Original screenshots are available in:

Screenshots/Safe-**MITM**/

### Screenshot Organization

All original practical screenshots are organized by activity:

Screenshots/ │ ├── Wireshark/ │ ├── Nmap/ │ ├── Packet-Tracer/ │ └── Safe-**MITM**/

These screenshots serve as supporting evidence for the practical work completed during Week 2.

### Intern Details

Name: **SAMYUKTHA** S Intern ID: DG/**SEPTEMBER**/**CYBER**/**102** Track: Cybersecurity Internship: DG Interns Hub Cybersecurity Internship Assignment: Week 2 — Advanced Networking, Analysis & Security Concepts