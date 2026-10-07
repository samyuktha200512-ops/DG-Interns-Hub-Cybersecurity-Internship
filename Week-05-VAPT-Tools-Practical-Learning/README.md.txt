<div align="center">

# 🔐 Week 5 – VAPT Tools Practical Learning

### DG Interns Hub Cybersecurity Internship

![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-198754?style=for-the-badge)
![VAPT](https://img.shields.io/badge/Focus-VAPT-0f5132?style=for-the-badge)
![Nmap](https://img.shields.io/badge/Tool-Nmap-198754?style=for-the-badge)
![Nikto](https://img.shields.io/badge/Tool-Nikto-0f5132?style=for-the-badge)
![Burp Suite](https://img.shields.io/badge/Tool-Burp%20Suite-198754?style=for-the-badge)

</div>

---

## 📌 Overview

This repository contains the practical work completed for **Week 5 – VAPT Tools Practical Learning** as part of the **DG Interns Hub Cybersecurity Internship**.

The work focuses on practical **Vulnerability Assessment and Penetration Testing (VAPT)** using Nmap, Nikto, and Burp Suite, followed by finding validation, security hardening, and retesting in an authorized lab environment.

---

## 🎯 Objective

To gain practical experience in VAPT by performing:

- Network and service enumeration
- Web server security assessment
- HTTP request analysis
- Security finding validation
- Basic security hardening
- Before-and-after security testing

---

## 🛠️ Tools Used

| Tool | Purpose |
|---|---|
| **Nmap** | Network and service enumeration |
| **Nikto** | Web server security assessment |
| **Burp Suite** | HTTP request interception and analysis |
| **cURL** | HTTP response and header validation |
| **Apache** | Web server used in the authorized Ubuntu lab |
| **Ubuntu Linux** | Authorized testing environment |
| **Git & GitHub** | Version control and documentation |

---

## 🎯 Assessment Scope

### Official Assignment Target

```text
http://testphp.vulnweb.com
```

The official assignment target was tested using the required VAPT tools.

Due to connectivity limitations from the available network path, the target could not be successfully accessed for complete HTTP-level testing.

The observed connection failures are documented as **testing limitations** and are not treated as evidence that the target is secure or free from vulnerabilities.

### Authorized Ubuntu Lab

An additional authorized Ubuntu lab environment was used to complete the practical VAPT workflow.

**Target:**

```text
192.168.162.131
```

The Ubuntu environment was used for:

- Nmap enumeration
- Nikto scanning
- Burp Suite request analysis
- Finding validation
- Security hardening
- Retesting

---

## 🔎 VAPT Workflow

```text
Nmap
  ↓
Nikto
  ↓
Burp Suite
  ↓
Finding Validation
  ↓
Security Hardening
  ↓
Retesting
  ↓
Before / After Comparison
```

---

## 🔍 Practical Work

### 1. Nmap Assessment

The following Nmap assessments were performed:

- SYN scan
- Service/version detection
- Advanced assessment
- Full TCP port scan

The authorized Ubuntu lab identified:

```text
22/tcp  SSH
80/tcp  HTTP
```

Service/version detection identified:

```text
OpenSSH 10.2p1 Ubuntu
Apache httpd 2.4.66 (Ubuntu)
```

---

### 2. Nikto Assessment

Nikto was used to assess the web server configuration and identify security-related observations.

The authorized Ubuntu lab produced observations related to:

- ETag information disclosure
- Missing defensive HTTP security headers
- HTTP methods allowed by the server

---

### 3. Burp Suite Analysis

Burp Suite was used to intercept and inspect HTTP communication.

The practical work included:

- Capturing an HTTP GET request
- Inspecting request headers
- Forwarding the request
- Inspecting the Apache HTTP response

---

## ⚠️ Validated Findings

### 1. ETag Information Disclosure

The Apache server exposed an ETag value through the HTTP response.

The observation was validated using HTTP header inspection.

This is documented as an **information disclosure/configuration observation** without claiming exploitability of the referenced CVE.

---

### 2. Missing Defensive Security Headers

The baseline HTTP response lacked several recommended security headers:

- `Content-Security-Policy`
- `Referrer-Policy`
- `X-Content-Type-Options`
- `Permissions-Policy`

These headers were subsequently configured and verified after hardening.

> **Note:** HSTS was not treated as a confirmed finding because the local practical test environment used HTTP and did not establish HTTPS.

---

### 3. Unnecessary HTTP Methods

The baseline server response allowed:

```text
GET
POST
OPTIONS
HEAD
```

The HTTP-method configuration was hardened to restrict unnecessary methods.

After hardening, an `OPTIONS` request returned:

```text
HTTP/1.1 403 Forbidden
```

This provided before-and-after validation of the configuration change.

---

## 🛡️ Security Hardening

The following defensive measures were implemented in the authorized Ubuntu lab:

- Added defensive HTTP security headers
- Disabled ETag generation using Apache configuration
- Restricted unnecessary HTTP methods
- Validated Apache configuration
- Reloaded Apache after configuration changes
- Verified Apache service status
- Performed post-hardening retesting

---

## 📊 Before & After Validation

The practical evidence includes before-and-after validation for:

- HTTP security headers
- ETag behavior
- HTTP method behavior
- Apache configuration
- Apache service/reload status
- Post-hardening HTTP responses

The retesting was performed to verify that the implemented security controls produced the expected results.

---

## 📂 Repository Structure

```text
Week-05-VAPT-Tools-Practical-Learning/
│
├── 01-Nmap/
│   ├── 01-Nmap-Version.png
│   ├── 02-Nmap-SYN-Baseline.png
│   ├── 03-Nmap-Service-Version.png
│   ├── 04-Nmap-Advanced-A.png
│   └── 05-Nmap-Full-TCP.png
│
├── 02-Nikto/
│   ├── 01-Nikto-Retry-Official-Target.png
│   └── 02-ZAP-Official-Target-Connection-Failure.png
│
├── 03-Burp-Suite/
│   ├── 01-Burp-Official-Target-GET-Request.png
│   └── 02-Burp-Official-Target-Connection-Failure.png
│
├── 04-Ubuntu-Lab/
│   ├── 01-Nmap/
│   ├── 02-Nikto/
│   ├── 03-Burp-Suite/
│   ├── 04-Findings/
│   └── 05-Defense-Hardening/
│
├── 05-Report/
│   └── Week-05-VAPT-Advanced-Practical-Report.pdf
│
├── 06-Presentation/
│   └── DG-Interns-Hub-Week-5-VAPT-Tools-Practical-Learning.pptx
│
└── README.md
```

---

## 🧠 Key Learning

This practical provided hands-on experience in:

- Network and service enumeration
- Web server security assessment
- HTTP request interception
- Security finding validation
- Evidence-based VAPT
- Apache security hardening
- Before-and-after security testing
- Technical security documentation

---

## 📸 Evidence

All practical screenshots and supporting evidence are organized in their respective folders.

### 📄 Final Report

`05-Report/Week-05-VAPT-Advanced-Practical-Report.pdf`

### 🎞️ Presentation

`06-Presentation/DG-Interns-Hub-Week-5-VAPT-Tools-Practical-Learning.pptx`

---

## 🔐 Disclaimer

All testing was performed against the specified assignment target and an authorized local Ubuntu lab environment for educational purposes.

No unauthorized systems were intentionally targeted.

---

<div align="center">

### 🚀 DG Interns Hub Cybersecurity Internship

**Week 5 — VAPT Tools Practical Learning**

</div>
