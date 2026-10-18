
# Week 7 – VAPT: Web Application Testing with Burp Suite

## 📌 Overview

This week focused on practical web application security testing using **Burp Suite Community Edition** against a locally hosted **Damn Vulnerable Web Application (DVWA)** lab. The activities covered HTTP/HTTPS interception, attack-surface mapping, manual vulnerability testing, endpoint discovery, and security documentation.

## 🎯 Objectives

- Configure Burp Suite to intercept browser traffic.
- Explore the DVWA site map and document the attack surface.
- Use Proxy and Repeater for manual request testing.
- Investigate SQL Injection, Reflected XSS, and Stored XSS in the lab.
- Explore Intruder payload positions and parameter modification.
- Capture evidence and document security recommendations.

## 🧪 Lab Environment

| Component | Details |
|---|---|
| Proxy tool | Burp Suite Community Edition |
| Target application | Damn Vulnerable Web Application (DVWA) |
| Target scope | Local lab (`127.0.0.1`) |
| Testing approach | Manual, controlled testing |

## 📂 Project Structure

```text
Week-07-Burp-Suite-Web-Application-Testing/
├── 01-Setup-Interception/
├── 02-Recon-Mapping/
├── 03-Vulnerability-Testing/
├── 04-Endpoint-Discovery/
├── 05-Report/
│   └── Week-07-VAPT-Report.pdf
├── 06-Presentation/
│   └── Week-07-VAPT-Presentation.pptx
└── README.md
```

## 🔍 Practical Activities

### 1. Setup and Interception
- Intercepted browser traffic using Burp Suite.
- Examined a login POST request.
- Captured evidence of HTTPS traffic interception.

### 2. Reconnaissance and Attack-Surface Mapping
- Explored the DVWA site map.
- Recorded observed application routes.
- Documented the attack surface in `Attack-Surface.txt`.

### 3. Vulnerability Testing
- Demonstrated SQL Injection behaviour in the local DVWA lab.
- Tested Reflected Cross-Site Scripting (XSS).
- Tested Stored Cross-Site Scripting (XSS).
- Configured Intruder payload positions for inspection.
- Modified a request parameter and examined the response.

### 4. Endpoint Discovery
- Reviewed endpoints visible through application navigation and Burp's site map.
- Captured the endpoint map.
- Documented observations in `Endpoint-Notes.txt`.

## 🛡️ Key Observations

- SQL Injection behaviour was demonstrated in the deliberately vulnerable lab.
- Reflected XSS was demonstrated in the lab.
- Stored XSS was demonstrated in the lab.
- Intruder payload positions were configured; this alone does not establish a successful brute-force attack.
- A modified parameter request was examined; this alone does not confirm broken access control.

These observations apply to the local DVWA environment and should not be interpreted as confirmed vulnerabilities in a production application.

## 📑 Deliverables

- **Technical report:** `05-Report/Week-07-VAPT-Report.pdf`
- **Presentation:** `06-Presentation/Week-07-VAPT-Presentation.pptx`
- **Evidence:** Screenshots organised in the practical activity folders.
- **Supporting notes:** Attack-surface and endpoint documentation.

## 🔐 Scope and Safety

All practical testing was limited to the locally hosted DVWA lab. Testing of third-party or production systems is not claimed. Use intentionally vulnerable applications only in authorised environments.

## ✅ Conclusion

This exercise provided practical experience with Burp Suite interception, HTTP request analysis, manual web vulnerability testing, endpoint mapping, evidence collection, and technical reporting.

---

**Internship:** DG Interns Hub – Cybersecurity Internship  
**Week:** 7  
**Topic:** VAPT – Web Application Testing with Burp Suite
