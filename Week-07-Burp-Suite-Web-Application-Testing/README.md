# Week 7 – VAPT: Web Application Testing with Burp Suite

### DG Interns Hub Cybersecurity Internship

![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-198754?style=flat-square)
![VAPT](https://img.shields.io/badge/Focus-Web%20Application%20Testing-0f5132?style=flat-square)
![Week 7](https://img.shields.io/badge/Internship-Week%207-198754?style=flat-square)
![Burp Suite](https://img.shields.io/badge/Tool-Burp%20Suite-0f5132?style=flat-square)

---

## 1. Overview

This repository documents the practical work completed during **Week 7 – VAPT: Web Application Testing with Burp Suite** as part of the DG Interns Hub Cybersecurity Internship.

The practical focused on web application security testing using Burp Suite Community Edition against a locally hosted Damn Vulnerable Web Application (DVWA) lab.

The activities covered HTTP/HTTPS traffic interception, application reconnaissance, attack-surface mapping, manual vulnerability testing, endpoint discovery, request manipulation, and security documentation.

## 2. Objectives

- Configure Burp Suite to intercept browser traffic.
- Explore the DVWA site map and document the application attack surface.
- Use Proxy and Repeater for manual request testing.
- Investigate SQL Injection, Reflected XSS, and Stored XSS in the local lab.
- Explore Intruder payload positions and parameter modification.
- Capture practical evidence and document security observations.
- Prepare technical documentation and recommendations.

## 3. Lab Environment and Assessment Scope

The practical activities were performed against a locally hosted DVWA application.

| Component | Details |
|---|---|
| Proxy tool | Burp Suite Community Edition |
| Target application | Damn Vulnerable Web Application (DVWA) |
| Target scope | Local lab (`127.0.0.1`) |
| Testing approach | Manual and controlled testing |
| Assessment focus | Web application security |

All testing was limited to the authorized local training environment.

## 4. Tools and Technologies

| Tool / Technology | Purpose |
|---|---|
| Burp Suite Community Edition | HTTP/HTTPS interception and manual request analysis |
| Burp Proxy | Intercepting and inspecting browser traffic |
| Burp Repeater | Modifying and replaying HTTP requests |
| Burp Intruder | Exploring payload positions and parameter modification |
| DVWA | Intentionally vulnerable web application for practical testing |
| Web Browser | Accessing the local application and generating requests |
| Git & GitHub | Version control and documentation |

## 5. Practical Tasks

### Task 1 – Setup and HTTP/HTTPS Interception

Burp Suite Community Edition was configured to intercept browser traffic generated while accessing the local DVWA application.

The activities included:

- Intercepting browser requests.
- Examining a login POST request.
- Inspecting HTTP request and response details.
- Capturing evidence of HTTPS traffic interception.

This exercise provided practical exposure to how web proxy tools can be used to inspect application-layer communication.

### Task 2 – Reconnaissance and Attack-Surface Mapping

The DVWA application was explored using Burp Suite's site map.

The activities included:

- Navigating the application.
- Reviewing routes observed through application navigation.
- Recording the available application paths.
- Documenting the observed attack surface.

The collected information was saved in:

```text
Attack-Surface.txt
```

The documentation represents routes observed during the practical exploration, not an exhaustive inventory of every possible application endpoint.

### Task 3 – Manual Vulnerability Testing

Manual testing was performed against the local DVWA application.

The practical activities covered the following areas:

#### SQL Injection

SQL Injection behaviour was demonstrated in the deliberately vulnerable DVWA environment.

#### Reflected Cross-Site Scripting (XSS)

Reflected XSS was tested in the local application, and the behaviour was demonstrated.

#### Stored Cross-Site Scripting (XSS)

Stored XSS was tested in the local application, and the behaviour was demonstrated.

#### Intruder Payload Position Configuration

Burp Suite Intruder was explored by configuring payload positions for request inspection.

Configuring payload positions does not, by itself, establish that a brute-force attack was successfully performed.

#### Parameter Modification

A request parameter was modified and the resulting application response was examined.

This activity provided exposure to request manipulation and response analysis. It does not independently confirm broken access control or another authorization vulnerability.

### Task 4 – Endpoint Discovery

The application endpoints visible through normal navigation and Burp Suite's site map were reviewed.

The activities included:

- Exploring application routes.
- Reviewing endpoints visible in the site map.
- Capturing the endpoint map.
- Recording endpoint-related observations.

Supporting documentation was saved in:

```text
Endpoint-Notes.txt
```

The endpoint documentation reflects the routes observed during the lab exercise.

## 6. Key Observations and Results

| Activity | Observation | Result |
|---|---|---|
| SQL Injection | SQL Injection behaviour demonstrated in DVWA | Demonstrated in local lab |
| Reflected XSS | Reflected XSS behaviour demonstrated | Demonstrated in local lab |
| Stored XSS | Stored XSS behaviour demonstrated | Demonstrated in local lab |
| Intruder | Payload positions configured for inspection | Configuration explored |
| Parameter modification | Modified request parameter and examined response | Request analysis performed |
| Attack-surface mapping | Application routes recorded from the site map | Documentation captured |
| Endpoint discovery | Observed endpoints documented | Notes captured |

### Important Scope Clarifications

- SQL Injection, Reflected XSS, and Stored XSS demonstrations apply to the deliberately vulnerable local DVWA environment.
- Intruder payload-position configuration does not establish a successful brute-force attack.
- A modified request parameter and its response do not independently confirm broken access control.
- The observed routes do not represent a guaranteed exhaustive endpoint inventory.
- No testing of third-party or production applications is claimed.

## 7. Evidence and Technical Documentation

Practical screenshots and supporting notes are organized by activity.

The documentation includes:

- Burp Suite setup and interception evidence.
- Reconnaissance and site-map screenshots.
- Vulnerability-testing screenshots.
- Endpoint discovery evidence.
- Attack-surface documentation.
- Technical report and presentation.

These materials provide supporting evidence for the activities performed during the practical.

## 8. Repository Structure

```text
Week-07-Burp-Suite-Web-Application-Testing/
│
├── 01-Setup-Interception/
│
├── 02-Recon-Mapping/
│
├── 03-Vulnerability-Testing/
│
├── 04-Endpoint-Discovery/
│
├── 05-Report/
│   └── Week-07-VAPT-Report.pdf
│
├── 06-Presentation/
│   └── Week-07-VAPT-Presentation.pptx
│
└── README.md
```

## 9. Deliverables

### Technical Report

`05-Report/Week-07-VAPT-Report.pdf`

### Presentation

`06-Presentation/Week-07-VAPT-Presentation.pptx`

### Practical Evidence

Screenshots are organized in the respective activity folders.

### Supporting Documentation

- `Attack-Surface.txt`
- `Endpoint-Notes.txt`

These files document the application routes and endpoints observed during the practical.

## 10. Key Learning Outcomes

Through this practical, I gained experience in:

- Configuring Burp Suite for browser traffic interception.
- Inspecting HTTP and HTTPS communication.
- Understanding login POST requests and request structure.
- Exploring application routes through Burp Suite's site map.
- Documenting an observed web application attack surface.
- Demonstrating SQL Injection and XSS behaviour in a controlled lab.
- Using Burp Repeater for manual request analysis.
- Exploring Intruder payload positions.
- Modifying request parameters and examining application responses.
- Recording endpoint observations and maintaining technical evidence.

## 11. Scope and Safety

All practical testing was limited to the locally hosted DVWA training environment.

DVWA is intentionally vulnerable and designed for educational security testing. Burp Suite and other security testing tools must only be used against systems you own or have explicit permission to assess.

Testing third-party or production systems without authorization is not part of this project.

## 12. Conclusion

Week 7 provided practical experience with Burp Suite-based web application testing in a controlled DVWA environment.

The activities covered traffic interception, application reconnaissance, attack-surface mapping, manual vulnerability demonstrations, request manipulation, endpoint discovery, and technical documentation.

The exercise reinforced the importance of understanding HTTP communication, validating application behaviour, maintaining evidence, and clearly distinguishing demonstrated results from unverified security assumptions.
