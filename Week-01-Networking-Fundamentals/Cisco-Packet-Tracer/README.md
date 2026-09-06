# Cisco Packet Tracer — Week 1

![Cisco Packet Tracer](https://img.shields.io/badge/Cisco%20Packet%20Tracer-Network%20Implementation-00BFFF?style=for-the-badge)
![Week](https://img.shields.io/badge/Week%2001-Networking%20Fundamentals-0A0A0A?style=for-the-badge)

**Intern:** SAMYUKTHA S  
**Intern ID:** DG/SEPTEMBER/CYBER/102

---

## Overview

This folder contains my Cisco Packet Tracer implementation completed as part of the Week 1 Networking Fundamentals assignment.

---

## Network Topology

The topology consists of:

**PC → 2960-24TT Switch → 2911 Router**

---

## IP Configuration

| Device | Configuration |
|---|---|
| PC | `192.168.1.10` |
| Subnet Mask | `255.255.255.0` |
| Default Gateway | `192.168.1.1` |
| Router GigabitEthernet0/0 | `192.168.1.1` |

---

## Connectivity Test

Connectivity was tested by sending a ping from the PC to the router:

```text
ping 192.168.1.1