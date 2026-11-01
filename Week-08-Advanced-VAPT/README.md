# Week 8 – Advanced VAPT: Attack Chain & Full Exploitation Project

### DG Interns Hub Cybersecurity Internship

![Cybersecurity](https://img.shields.io/badge/Domain-Cybersecurity-198754?style=flat-square)
![VAPT](https://img.shields.io/badge/Focus-Advanced%20VAPT-0f5132?style=flat-square)
![Week 8](https://img.shields.io/badge/Internship-Week%208-198754?style=flat-square)
![OWASP Juice Shop](https://img.shields.io/badge/Target-OWASP%20Juice%20Shop-0f5132?style=flat-square)
![Burp Suite](https://img.shields.io/badge/Tool-Burp%20Suite-198754?style=flat-square)

---

## 1. Overview

This repository documents the practical work completed during **Week 8 – Advanced VAPT: Attack Chain & Full Exploitation Project** as part of the DG Interns Hub Cybersecurity Internship.

The project focused on web application security testing using a locally hosted OWASP Juice Shop environment and Burp Suite.

The practical activities involved inspecting HTTP requests and responses, identifying application security weaknesses, analyzing potential attack paths, assessing security impact, documenting findings, and preparing remediation and retesting recommendations.

The assessment followed an evidence-based approach, distinguishing demonstrated application behavior from potential security impact and unverified exploitation scenarios.

## 2. Objectives

- Identify and document application security weaknesses.
- Inspect HTTP requests and responses using Burp Suite.
- Assess observed application behavior and potential security impact.
- Analyze potential attack paths and related security risks.
- Map findings to relevant security concerns.
- Recommend remediation measures.
- Prepare retesting steps and technical documentation.
- Maintain evidence to support security findings.

## 3. Lab Environment and Assessment Scope

The practical assessment was performed against a locally hosted OWASP Juice Shop application.

| Component | Details |
|---|---|
| Target application | OWASP Juice Shop |
| Environment | Local lab |
| Testing tool | Burp Suite |
| Assessment type | Web application security testing |
| Scope | Authorized testing of the locally hosted application |

All testing activities were limited to the intentionally vulnerable local training application.

## 4. Tools and Technologies

| Tool / Technology | Purpose |
|---|---|
| OWASP Juice Shop | Local web application security testing environment |
| Burp Suite | HTTP request and response inspection |
| Web Browser | Application interaction and testing |
| Git & GitHub | Version control and technical documentation |

## 5. Practical Assessment Workflow

The project followed an evidence-driven web application testing process:

```text
        Application Exploration
                 |
                 v
        Attack-Surface Mapping
                 |
                 v
       HTTP Request Inspection
                 |
                 v
       Security Behavior Testing
                 |
                 v
        Evidence Collection
                 |
                 v
       Finding Identification
                 |
                 v
          Risk Assessment
                 |
                 v
       Remediation Recommendations
                 |
                 v
          Retest Planning
                 |
                 v
       Technical Documentation
```

## 6. Key Findings and Observations

The assessment documented two application security findings in the local OWASP Juice Shop environment.

### Finding F-01 – SQL Error Disclosure in Product Search

**Observation:**

A malformed product-search input caused the application to return a database error and stack-trace details.

This demonstrated error disclosure and indicated potentially unsafe query handling.

**Evidence:**

- Malformed product-search input.
- Database error returned by the application.
- Stack-trace details exposed in the response.

**Potential Security Impact:**

Detailed database errors and stack traces may reveal internal application implementation details. Such information could help an attacker understand the application's backend and identify areas for further investigation.

However, successful SQL Injection or database extraction was not demonstrated during this assessment.

**Recommended Remediation:**

- Use parameterized queries or prepared statements.
- Avoid exposing database errors and stack traces in client-facing responses.
- Return generic error messages to users.
- Retain detailed diagnostic information only in secure server-side logs.
- Retest the product-search functionality after remediation.

### Finding F-02 – Admin Role Assignment During Registration

**Observation:**

During registration testing, the application accepted a client-supplied `admin` role.

The local lab confirmed the Admin Registration challenge.

**Evidence:**

- Registration request inspection.
- Client-supplied role value.
- Confirmation of the Admin Registration challenge in the local lab.

**Potential Security Impact:**

Accepting privilege-related values from client-controlled input may create a privilege-assignment weakness. If server-side authorization controls are insufficient, this behavior could potentially allow unauthorized privilege assignment.

Access to protected administrative operations was not independently demonstrated during this assessment.

**Recommended Remediation:**

- Assign user roles exclusively through server-side logic.
- Reject or ignore client-supplied privilege fields during registration.
- Enforce authorization checks on protected operations.
- Apply least-privilege principles to user accounts.
- Retest registration and authorization behavior after remediation.

## 7. Findings Summary

| Finding ID | Finding | Observed Behavior | Validation Scope |
|---|---|---|---|
| F-01 | SQL Error Disclosure | Malformed product-search input exposed database errors and stack-trace details | Error disclosure demonstrated; SQL Injection and database extraction not demonstrated |
| F-02 | Admin Role Assignment During Registration | Client-supplied `admin` role was accepted during registration | Admin Registration challenge confirmed; protected administrative operations not independently tested |

The findings are documented according to the available evidence. Potential impact is distinguished from functionality that was not independently demonstrated.

## 8. Remediation and Retesting Plan

The project includes remediation recommendations and planned retesting activities.

| Finding | Recommended Remediation | Planned Retesting |
|---|---|---|
| F-01 – SQL Error Disclosure | Use parameterized queries and generic client-facing error messages | Submit malformed search input and verify that internal database errors and stack traces are no longer exposed |
| F-02 – Admin Role Assignment | Enforce server-side role assignment and authorization checks | Attempt client-side role manipulation and verify that unauthorized privilege assignment is rejected |

**Remediation status:** The fixes and retesting activities are documented as recommendations and planned follow-up work. They should not be considered completed until implementation and verification evidence is available.

## 9. Evidence and Technical Documentation

The project includes supporting materials documenting the assessment process and findings.

The evidence and documentation cover:

- Attack-surface and route inventory notes.
- Burp Suite request and response screenshots.
- Attack-chain analysis.
- Finding reports and risk assessment.
- Security test matrix.
- Remediation recommendations.
- Retesting plan.
- Final technical report and presentation.

These materials support the documented observations and provide a record of the practical assessment.

## 10. Repository Structure

The project documentation is organized around the assessment evidence and deliverables.

The repository includes:

- Attack-surface and route inventory notes.
- Burp Suite request/response evidence.
- Attack-chain analysis.
- Finding documentation.
- Risk assessment and security test matrix.
- Remediation and retest plan.
- Final technical report.
- Presentation.

The exact folder and file names should be maintained according to the actual repository contents.

## 11. Key Learning Outcomes

Through this practical, I gained experience in:

- Performing web application security testing in a controlled environment.
- Inspecting HTTP requests and responses using Burp Suite.
- Identifying information disclosure through application error responses.
- Investigating client-controlled registration parameters.
- Understanding the security implications of improper role assignment.
- Assessing potential application security impact.
- Separating demonstrated behavior from unverified exploitation claims.
- Collecting and organizing technical evidence.
- Preparing vulnerability findings and risk assessments.
- Developing remediation recommendations and retesting plans.

## 12. Scope and Safety

All testing was conducted against a locally hosted OWASP Juice Shop training application for educational purposes.

OWASP Juice Shop is an intentionally vulnerable application designed for security learning and practice.

Security testing tools must only be used against systems you own or have explicit authorization to assess. No unauthorized third-party or production system testing is claimed as part of this project.

## 13. Conclusion

Week 8 provided practical experience in advanced web application security testing using OWASP Juice Shop and Burp Suite.

The project focused on identifying and documenting SQL error disclosure and client-controlled administrative role assignment behavior, analyzing potential security impact, and preparing remediation and retesting recommendations.

The exercise reinforced the importance of evidence-based vulnerability reporting, understanding application trust boundaries, assessing authorization-related risks, and distinguishing confirmed observations from unverified exploitation scenarios.
