# Week 5 – VAPT Tools Practical Learning

### DG Interns Hub Cybersecurity Internship

![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-198754?style=flat-square)
![VAPT](https://img.shields.io/badge/Focus-VAPT-0f5132?style=flat-square)
![Week 5](https://img.shields.io/badge/Internship-Week%205-198754?style=flat-square)
![Nmap](https://img.shields.io/badge/Tool-Nmap-198754?style=flat-square)
![Nikto](https://img.shields.io/badge/Tool-Nikto-0f5132?style=flat-square)
![Burp Suite](https://img.shields.io/badge/Tool-Burp%20Suite-198754?style=flat-square)

---

## 1. Overview

This repository documents the practical work completed during **Week 5 – VAPT Tools Practical Learning** as part of the DG Interns Hub Cybersecurity Internship.

The work focused on applying Vulnerability Assessment and Penetration Testing (VAPT) tools, including Nmap, Nikto, and Burp Suite. The practical workflow covered network and service enumeration, web server assessment, HTTP traffic inspection, finding validation, security hardening, and post-hardening retesting.

An authorized Ubuntu lab environment was used to complete the practical workflow when connectivity limitations prevented complete HTTP-level testing of the official assignment target.

## 2. Objectives

- Perform network and service enumeration.
- Assess web server configuration using Nikto.
- Inspect HTTP requests and responses using Burp Suite.
- Identify and validate security-related observations.
- Apply basic Apache security hardening.
- Compare baseline and post-hardening configurations.
- Document findings with supporting evidence.

## 3. Assessment Scope and Lab Environment

### Official Assignment Target

```text
http://testphp.vulnweb.com
```

The official assignment target was used for the required assessment attempts.

Due to connectivity limitations along the available network path, complete HTTP-level testing could not be performed successfully. The connection failures are documented as testing limitations and are not treated as evidence that the target is secure or free from vulnerabilities.

### Authorized Ubuntu Lab

**Target IP:**

```text
192.168.162.131
```

An additional authorized Ubuntu environment was used to complete the practical VAPT workflow.

The lab was used for:

- Nmap enumeration
- Nikto web server assessment
- Burp Suite HTTP request analysis
- Finding validation
- Apache security hardening
- Post-hardening retesting

The configuration findings and hardening activities described in this README relate to this authorized lab unless otherwise stated.

## 4. Tools and Technologies

| Tool / Technology | Purpose |
|---|---|
| Nmap | Network discovery, port scanning, and service/version detection |
| Nikto | Web server security assessment |
| Burp Suite | HTTP request interception and response analysis |
| cURL | HTTP response and header validation |
| Apache | Web server used in the Ubuntu lab |
| Ubuntu Linux | Authorized testing environment |
| Git and GitHub | Version control and documentation |

## 5. Practical Tasks

### Task 1 – Nmap Assessment

Nmap was used to examine the authorized Ubuntu lab and identify exposed network services.

The assessment included:

- SYN scanning
- Service and version detection
- Advanced assessment
- Full TCP port scanning

**Identified services:**

| Port | Service |
|---|---|
| 22/tcp | SSH |
| 80/tcp | HTTP |

**Service/version information:**

```text
OpenSSH 10.2p1 Ubuntu
Apache httpd 2.4.66 (Ubuntu)
```

The results provided an overview of the services exposed by the lab system.

### Task 2 – Nikto Assessment

Nikto was used to assess the web server configuration and identify security-related observations.

The authorized Ubuntu lab produced observations involving:

- ETag information exposure
- Missing recommended HTTP security headers
- HTTP methods permitted by the server

These observations were reviewed further rather than automatically treating every scanner output as a confirmed exploitable vulnerability.

### Task 3 – Burp Suite Analysis

Burp Suite was used to inspect HTTP communication during the practical.

The activities included:

- Capturing an HTTP GET request
- Inspecting request headers
- Forwarding the request
- Examining the Apache HTTP response

This provided practical exposure to HTTP request and response analysis.

## 6. Findings and Observations

The following observations were identified and validated in the authorized Ubuntu lab.

### Finding 1 – ETag Information Exposure

**Observation:** The Apache server exposed an ETag value in its HTTP response.

**Validation:** HTTP response headers were inspected to verify the presence of the ETag information.

**Remediation:** ETag generation was disabled through Apache configuration.

**Verification:** The server was retested after the configuration change.

This is documented as an information exposure/configuration observation. The presence of an ETag alone does not establish exploitability of a specific CVE.

### Finding 2 – Missing Defensive HTTP Security Headers

**Observation:** The baseline HTTP response did not contain several recommended defensive security headers.

| Header | Security Purpose |
|---|---|
| Content-Security-Policy | Helps control the sources from which browser content can be loaded |
| Referrer-Policy | Controls referrer information sent with requests |
| X-Content-Type-Options | Helps prevent MIME-type sniffing |
| Permissions-Policy | Controls access to selected browser features |

**Remediation:** The identified headers were configured in Apache.

**Verification:** HTTP response headers were checked again after hardening.

**Scope note:** HSTS was not treated as a confirmed finding because the local practical environment used HTTP and did not establish HTTPS.

### Finding 3 – Unnecessary HTTP Methods

**Observation:** The baseline server response indicated that the following HTTP methods were allowed:

```text
GET
POST
OPTIONS
HEAD
```

**Remediation:** The Apache HTTP-method configuration was hardened to restrict unnecessary methods.

**Post-hardening validation:**

An OPTIONS request returned:

```text
HTTP/1.1 403 Forbidden
```

This provided evidence that the method restriction was taking effect after the configuration change.

## 7. Security Hardening and Retesting

The following defensive configuration changes were implemented in the authorized Ubuntu lab:

| Area | Hardening Action |
|---|---|
| HTTP security headers | Added the selected defensive response headers |
| ETag configuration | Disabled ETag generation |
| HTTP methods | Restricted unnecessary HTTP methods |
| Apache configuration | Validated configuration before applying changes |
| Apache service | Reloaded Apache after configuration updates |
| Verification | Checked service status and retested HTTP responses |

Post-hardening testing was performed to compare the baseline behavior with the updated server configuration.

| Assessment Area | Baseline Observation | Post-Hardening Verification |
|---|---|---|
| HTTP security headers | Selected headers were missing | Configured headers checked in the response |
| ETag | ETag information exposed | ETag behavior retested |
| HTTP methods | GET, POST, OPTIONS, HEAD allowed | OPTIONS returned 403 Forbidden |
| Apache configuration | Baseline configuration | Configuration validated after changes |
| Apache service | Initial service state | Reload and service status verified |
| HTTP response | Baseline response captured | Post-hardening response inspected |

## 8. Repository Structure

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

## 9. Evidence and Deliverables

All practical screenshots and supporting evidence are organized in their respective folders.

### Technical Report

`05-Report/Week-05-VAPT-Advanced-Practical-Report.pdf`

### Presentation

`06-Presentation/DG-Interns-Hub-Week-5-VAPT-Tools-Practical-Learning.pptx`

The report and presentation document the assessment workflow, observations, validation activities, remediation, and practical outcomes.

## 10. Key Learning Outcomes

Through this practical, I gained experience in:

- Network and service enumeration using Nmap.
- Web server assessment using Nikto.
- HTTP request and response inspection using Burp Suite.
- Reviewing scanner observations and validating findings.
- Understanding defensive HTTP security headers.
- Applying basic Apache server hardening.
- Restricting unnecessary HTTP methods.
- Performing post-remediation verification.
- Maintaining evidence-based technical documentation.

## 11. Testing Scope and Disclaimer

All testing was conducted for educational purposes using the specified assignment target and an authorized local Ubuntu lab.

The official assignment target could not be fully assessed at the HTTP level because of connectivity limitations. The additional configuration findings and hardening activities were performed in the authorized Ubuntu environment.

No unauthorized systems were intentionally targeted. Scanner observations are documented within the limits of the available evidence and are not automatically treated as confirmed exploitable vulnerabilities.

## 12. Conclusion

Week 5 provided practical exposure to the VAPT workflow, from network enumeration and web server assessment to finding validation, defensive configuration changes, and retesting.

The exercise reinforced the importance of validating scanner observations, documenting evidence, and verifying the effectiveness of security hardening measures.
