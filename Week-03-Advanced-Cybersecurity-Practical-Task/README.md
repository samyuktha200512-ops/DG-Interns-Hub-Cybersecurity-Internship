🔐 DG Interns Hub — Week 03 Cybersecurity Practical Task

<div align=*center*>

![DG Interns Hub](https://img.shields.io/badge/DG%20Interns%20Hub-Cybersecurity-0A66C2?style=flat-square) ![Week 03](https://img.shields.io/badge/Week-03-6F42C1?style=flat-square) ![Status](https://img.shields.io/badge/Status-Completed-2EA44F?style=flat-square)

![Kali Linux](https://img.shields.io/badge/Kali-Linux-557C94?style=flat-square&logo=kalilinux&logoColor=white) ![Ubuntu](https://img.shields.io/badge/Ubuntu-Server-E95420?style=flat-square&logo=ubuntu&logoColor=white) ![Nmap](https://img.shields.io/badge/Nmap-Network%20Scanning-4682B4?style=flat-square) ![Wireshark](https://img.shields.io/badge/Wireshark-Traffic%20Analysis-1679A7?style=flat-square&logo=wireshark&logoColor=white) ![VMware](https://img.shields.io/badge/VMware-Virtual%20Lab-607078?style=flat-square&logo=vmware&logoColor=white) ![UFW](https://img.shields.io/badge/UFW-Firewall%20Hardening-8B5CF6?style=flat-square)

### Advanced Cybersecurity Practical Task

Real-World Network Security Assessment & Traffic Investigation

</div>

📌 Project Overview

This repository contains my Week 03 Advanced Cybersecurity Practical Task completed as part of the DG Interns Hub Cybersecurity Internship.

The practical focused on building and assessing an isolated virtual cybersecurity lab using Kali Linux and Ubuntu Server. The assessment covered host discovery, network scanning, service enumeration, operating-system detection, **TCP**/**UDP** analysis, Wireshark packet investigation, vulnerability-oriented assessment, security hardening, and before/after validation.

All activities were performed in an authorized, isolated laboratory environment using my own virtual machines.

🎯 Objectives

The main objectives of this practical were to:

Build an isolated cybersecurity laboratory.

Discover active systems within the authorized lab network.

Perform basic and advanced Nmap scanning.

Identify exposed services and service versions.

Analyze **TCP**, **UDP**, **ICMP**, **DNS** and **ARP** traffic using Wireshark.

Correlate Nmap results with packet-level evidence.

Investigate **TCP** flags, resets and retransmissions.

Perform an evidence-based vulnerability assessment.

Apply security hardening to the Ubuntu target.

Validate the hardening through before/after testing.

Complete a final mini security assessment.

🧪 Lab Environment

The practical was performed using VMware virtualization.

### Virtual Machines

System

Role

IP Address

### Kali Linux

Security analysis / scanning machine

**192**.**168**.**162**.**128**

### Ubuntu Server

Authorized target machine

**192**.**168**.**162**.**130**

Network

Network:      **192**.**168**.**162**.0/24 Subnet Mask:  **255**.**255**.**255**.0 Network Type: VMware Host-only / VMnet1

### Lab Architecture

    VMware Workstation
    │
    Host-only VMnet1
    **192**.**168**.**162**.0/24
    │
    ┌──────────────┴──────────────┐
    │                             │
    ┌──────▼──────┐               ┌──────▼──────┐
    │ Kali Linux  │               │ Ubuntu      │
    │ Scanner     │               │ Target      │
    │             │               │             │
    │ **192**.**168**.    │               │ **192**.**168**.    │
    │ **162**.**128**     │               │ **162**.**130**     │
    └─────────────┘               └─────────────┘
    │                             │
    └──── Nmap / Wireshark ──────┘

The detailed network topology diagram is available in the 03-Network-Topology/ directory.

🛠️ Tools Used

Tool

Purpose

### Kali Linux

Security testing and traffic analysis

### Ubuntu Server

Authorized target system

VMware Workstation

Virtualization and isolated lab networking

Nmap

Host discovery, port scanning and service assessment

Wireshark

Packet capture and traffic investigation

## **UFW**

Host firewall hardening

Netcat

Controlled **TCP**/**UDP** traffic generation

Ping / **ICMP**

Connectivity verification

## **SSH**

Secure remote-access testing

🔎 Task 7 — Network Discovery & Basic Nmap Scanning

7.1 Host Discovery

The authorized lab subnet was scanned using:

nmap -sn **192**.**168**.**162**.0/24

The scan identified four responsive addresses.

Relevant lab systems:

Kali Linux — **192**.**168**.**162**.**128**

Ubuntu Target — **192**.**168**.**162**.**130**

The remaining responsive addresses were identified as VMware-related virtual-network infrastructure.

Evidence

📁 04-Nmap/01-Network-Discovery.png

7.2 Basic **TCP** Scan

The Ubuntu target was scanned using:

nmap **192**.**168**.**162**.**130**

Result

22/tcp open ssh

Nmap also reported **999** closed **TCP** ports in its default scan.

Observation

The target was reachable and **SSH** was exposed on **TCP** port 22.

Evidence

📁 04-Nmap/02-Basic-Nmap-Scan.png

🔬 Task 8 — Advanced Nmap Security Assessment

8.1 Service & Version Detection

Command:

nmap -sV **192**.**168**.**162**.**130**

Result

22/tcp open ssh OpenSSH 10.2p1 Ubuntu 2ubuntu3.5

The scan also identified Linux-related service information.

Evidence

📁 04-Nmap/03-Nmap-Service-Version-Detection.png

8.2 Operating System Detection

Command:

nmap -O **192**.**168**.**162**.**130**

Result

Nmap reported:

No exact OS matches for host

A **TCP**/IP fingerprint was generated and network distance was reported as one hop.

Observation

The target is known to be Ubuntu from the lab configuration, but this particular Nmap OS detection attempt did not return an exact match.

Evidence

📁 04-Nmap/04-Nmap-OS-Detection.png

8.3 **TCP** **SYN** Scan

Command:

nmap -sS **192**.**168**.**162**.**130**

Result

22/tcp open ssh

Observation

The **SYN** scan produced a result consistent with the basic **TCP** scan.

Evidence

📁 04-Nmap/05-Nmap-**SYN**-Scan.png

8.4 **UDP** Top-20 Scan

Command:

nmap -sU --top-ports 20 **192**.**168**.**162**.**130**

Result

Several ports were reported as open|filtered, while others were closed.

No **UDP** port was conclusively identified as open during this assessment.

### Important Interpretation

open|filtered does not confirm that a **UDP** service is open. It indicates that Nmap could not distinguish between an open port and a filtered port from the available responses.

Evidence

📁 04-Nmap/06-Nmap-**UDP**-Top20.png

8.5 Vulnerability-Oriented **NSE** Scan

Command:

nmap --script vuln **192**.**168**.**162**.**130**

Result

No vulnerability findings were reported in the command output.

### Important Interpretation

This result does not prove that the target contains zero vulnerabilities. It only means that the selected Nmap vulnerability-oriented scripts did not report a finding during this assessment.

Evidence

📁 04-Nmap/07-Nmap-Vulnerability-Scripts.png

📡 Task 9 — Wireshark Network Traffic Capture

Wireshark was used to capture and analyze traffic on Kali's eth0 interface.

The following traffic types were investigated:

## **ICMP**

## **DNS**

## **TCP** / **SSH**

## **UDP**

## **ARP**

## **TCP** **SYN**

## **TCP** **RST**

9.1 **ICMP** Capture

The Kali and Ubuntu systems exchanged IPv4 **ICMP** echo requests and replies.

Observation

Four Echo Requests and corresponding Echo Replies were observed during the controlled ping test.

Evidence

📁 05-Wireshark/01-**ICMP**-Capture.png

9.2 **DNS** Capture

A controlled **DNS** lookup was generated and captured using Wireshark.

The traffic showed:

**DNS** Standard Query **DNS** Standard Query Response

Evidence

📁 05-Wireshark/02-**DNS**-Capture.png

9.3 **TCP** / **SSH** Capture

The **SSH** service on port 22 was observed during a controlled connection.

The capture showed:

## **SYN** **SYN**-**ACK** **ACK**

followed by **SSH** protocol negotiation and encrypted traffic.

Evidence

📁 05-Wireshark/03-**TCP**-**SSH**-Capture.png

9.4 **UDP** Capture

A controlled **UDP** packet was sent from Kali to Ubuntu on destination port **9999**.

Example

Kali:   **192**.**168**.**162**.**128** Ubuntu: **192**.**168**.**162**.**130** **UDP**:    **33655** → **9999**

Evidence

📁 05-Wireshark/04-**UDP**-Capture.png

9.5 **ARP** Capture

**ARP** traffic was captured during local address resolution.

Example:

Who has **192**.**168**.**162**.**130**?

The Ubuntu target responded with its **MAC** address.

Evidence

📁 05-Wireshark/05-**ARP**-Capture.png

9.6 **TCP** **SYN** Capture

**TCP** **SYN** activity was isolated using Wireshark filters.

The controlled **SSH** traffic showed:

## **SYN** **SYN**-**ACK**

Evidence

📁 05-Wireshark/06-**TCP**-**SYN**-Capture.png

9.7 **TCP** **RST** Capture

A controlled connection attempt to **TCP** port **9998** produced:

## **RST**, **ACK**

from the Ubuntu target.

Evidence

📁 05-Wireshark/07-**TCP**-**RST**-Capture.png

🔗 Task 10 — Nmap + Wireshark Investigation

A controlled Nmap **SYN** scan was performed against:

22/tcp **9998**/tcp

Command:

nmap -sS -p 22,**9998** **192**.**168**.**162**.**130**

### Nmap Result

22/tcp   open **9998**/tcp closed

### Wireshark Correlation

For port 22:

## **SYN** → **SYN**-**ACK** → **ACK**

For port **9998**:

## **SYN** → **RST**, **ACK**

Conclusion

The packet-level observations matched the Nmap port-state classifications.

Evidence

📁 06-Nmap-Wireshark-Investigation/

08-Task10-Nmap-Correlation.png

09-Task10-Wireshark-Correlation.png

🧭 Task 11 — Advanced Traffic Investigation

The traffic investigation examined:

Communication pairs

Observed protocols

**TCP** flags

**SYN** / **SYN**-**ACK** behavior

**RST** behavior

**TCP** retransmissions

Normal versus unexpected traffic patterns

### Communication Baseline

**192**.**168**.**162**.**128** ↔ **192**.**168**.**162**.**130**

### Observed Protocols

## **ICMP**

## **TCP**

## **SSH**

## **UDP**

## **ARP**

## **DNS**

**TCP** Investigation

The following behaviors were observed:

Normal connection: **SYN** → **SYN**-**ACK** → **ACK**

Closed port: **SYN** → **RST**, **ACK**

Retransmission: Repeated **TCP** transmission after the expected response was not received

Observed retransmissions were treated as network behavior requiring context rather than automatically being classified as malicious.

Evidence

📁 06-Nmap-Wireshark-Investigation/

and

📁 07-Advanced-Traffic-Investigation/

🛡️ Task 12 — Vulnerability Assessment

A baseline assessment was performed directly on the Ubuntu target.

Key checks

sudo ss -lntup sudo ufw status verbose sudo sshd -T | grep -E '^(permitrootlogin|passwordauthentication|pubkeyauthentication)' apt list --upgradable

Findings

Observation

Assessment

**SSH** on **TCP**/22

Exposed service / attack surface

**UFW** inactive

Security hardening gap

Password authentication enabled

Hardening opportunity

Root password login prohibited

Positive baseline

Public-key authentication enabled

Positive baseline

No pending package updates observed

No update issue identified

Nmap vulnerability scripts

No findings reported

Important conclusion

No confirmed vulnerability was established solely from these observations.

The strongest actionable findings were hardening gaps, especially the inactive firewall.

Evidence

📁 07-Vulnerability-Assessment/

📊 Task 12 — Risk Classification

The findings were considered according to their practical security impact.

Finding

Classification

Reason

**UFW** inactive

Medium hardening concern

No host-level filtering before hardening

Password authentication enabled

Medium hardening opportunity

Broader authentication exposure than key-only access

**SSH** on **TCP**/22

Attack surface

Required remote-management service

Root password login prohibited

Positive control

Reduces direct root password access

No Nmap vuln findings

Informational

Automated scan produced no reported findings

These classifications describe the observed lab configuration and are not intended as a formal production risk rating.

🔧 Task 13 — Security Hardening

The main hardening change was enabling **UFW** while explicitly allowing **SSH**.

Before

**UFW**: inactive

Configuration

sudo ufw allow ssh sudo ufw enable

After

**UFW**: active Logging: on (low) 22/tcp: **ALLOW** IN 22/tcp (v6): **ALLOW** IN

Evidence

📁 08-Security-Hardening/

🔄 Task 13 — Before / After Comparison

### Before Hardening

**UFW**: inactive

22/tcp → open → ssh **999** **TCP** ports → closed

### After Hardening

**UFW**: active

22/tcp → open → ssh **999** **TCP** ports → filtered

Interpretation

The firewall successfully changed the behavior of unsolicited inbound **TCP** traffic.

**SSH** remained available because **TCP**/22 was explicitly allowed.

Validation

**SSH** connectivity was successfully verified after enabling the firewall.

🧠 Task 14 — Final Mini Security Assessment

The final assessment combined:

Lab discovery

Nmap scanning

Service/version detection

OS detection

**TCP** and **UDP** assessment

Wireshark packet analysis

Nmap/Wireshark correlation

Vulnerability assessment

Security hardening

Before/after validation

### Final Target Baseline

Target: **192**.**168**.**162**.**130**

Primary exposed service: 22/tcp → **SSH**

Service: OpenSSH 10.2p1 Ubuntu 2ubuntu3.5

### Final Security State

**UFW**: Active

**SSH**: Accessible

Other scanned **TCP** ports: Filtered

The assessment demonstrated that enabling the host firewall reduced unsolicited network exposure while preserving the required administrative service.

✅ Key Learnings

Through this practical, I learned how to:

Build an isolated cybersecurity lab.

Use Nmap for structured network assessment.

Understand **TCP** port states.

Perform service and version detection.

Interpret OS-detection limitations.

Perform **TCP** **SYN** and **UDP** scanning.

Capture and analyze packets using Wireshark.

Understand **ICMP**, **DNS**, **ARP**, **TCP** and **UDP** traffic.

Correlate scanner output with packet-level evidence.

Investigate **SYN**, **RST** and retransmission behavior.

Perform evidence-based vulnerability assessment.

Apply firewall hardening.

Validate security improvements using before/after testing.

⚠️ Challenges Faced

## Host connectivity issue

At one stage, the expected **ICMP** traffic was not visible because the target was unreachable.

This was resolved by checking the interface configuration and restoring correct Host-only network connectivity.

## DNS capture issue

The Host-only VMware network did not provide a working **DNS** service for the **DNS** experiment.

A temporary **NAT** connection was used only to generate and capture legitimate **DNS** traffic, after which Kali was returned to the isolated Host-only network.

## Wireshark filtering

Some filters initially displayed unrelated background traffic or no matching packets.

This was resolved by narrowing filters to the required IP addresses, ports, and **TCP** flags.

## OS detection limitation

Nmap did not return an exact OS match.

Rather than forcing a conclusion, the result was documented as an inconclusive OS fingerprint.

🔐 Security Recommendations

Based on the lab assessment:

Keep host-based firewall protection enabled.

Allow only required services through the firewall.

Prefer **SSH** public-key authentication over password authentication.

Restrict **SSH** exposure to trusted networks wherever practical.

Continue monitoring unusual connection attempts and retransmissions.

Regularly review exposed services and listening ports.

Keep systems updated and verify security configuration after changes.

Reassess the system after significant configuration changes.

📁 Repository Structure

Week-3-Advanced-Cybersecurity-Practical-Task/ │ ├── 01-Report/ │   ├── Week-3-Final-Report-Advanced-Cover-Enhanced.pdf │   └── Week-3-Final-Report-Advanced-Cover-Enhanced.docx │ ├── 02-Presentation/ │   └── Week-3-Presentation-Advanced.pptx │ ├── 03-Network-Topology/ │   └── Week3-Advanced-Network-Topology.png │ ├── 04-Nmap/ │   ├── 01-Network-Discovery.png │   ├── 02-Basic-Nmap-Scan.png │   ├── 03-Nmap-Service-Version-Detection.png │   ├── 04-Nmap-OS-Detection.png │   ├── 05-Nmap-**SYN**-Scan.png │   ├── 06-Nmap-**UDP**-Top20.png │   └── 07-Nmap-Vulnerability-Scripts.png │ ├── 05-Wireshark/ │   ├── 01-**ICMP**-Capture.png │   ├── 02-**DNS**-Capture.png │   ├── 03-**TCP**-**SSH**-Capture.png │   ├── 04-**UDP**-Capture.png │   ├── 05-**ARP**-Capture.png │   ├── 06-**TCP**-**SYN**-Capture.png │   └── 07-**TCP**-**RST**-Capture.png │ ├── 06-Nmap-Wireshark-Investigation/ │   ├── 08-Task10-Nmap-Correlation.png │   └── 09-Task10-Wireshark-Correlation.png │ ├── 07-Vulnerability-Assessment/ │ ├── 08-Security-Hardening/ │ └── **README**.md

📄 Project Deliverables

### Final Report

A 15-page technical report covering the complete practical assessment.

Presentation

A 12-slide professional presentation summarizing the project, findings, traffic analysis, hardening and results.

### Network Topology

Advanced visual representation of the VMware Host-only cybersecurity lab.

Evidence

Real screenshots captured during the practical activities.

🔒 Scope & Safety

All activities in this repository were performed in an authorized, isolated laboratory environment using self-controlled virtual machines.

The practical was conducted for:

cybersecurity learning

network analysis

defensive security assessment

traffic investigation

hardening validation

No unauthorized systems were intentionally targeted.

📚 References

### Nmap Documentation

### Wireshark Documentation

### Ubuntu Server Documentation

Ubuntu OpenSSH Documentation

VMware Documentation

🎓 Internship Information

Program: DG Interns Hub Cybersecurity Internship Week: 03 Focus: Advanced Cybersecurity Practical Task Participant: **SAMYUKTHA** S. Internship ID: DG/**SEPTEMBER**/**CYBER**/**102**

🏁 Conclusion

This Week 03 practical provided hands-on experience in conducting a structured cybersecurity assessment within a controlled virtual environment.

The project progressed from network discovery and Nmap scanning to packet-level investigation with Wireshark, followed by vulnerability assessment, security hardening and before/after validation.

The most important learning was that security tools should be used together and their results should be interpreted using actual evidence. Nmap provided visibility into exposed ports and services, while Wireshark provided packet-level context. The hardening stage then demonstrated how a security control can measurably change network exposure without disrupting required connectivity.

<div align=*center*>

🔐 Stronger Networks. Safer Tomorrow.

DG Interns Hub — Cybersecurity Internship — Week 03

</div>
