# Week 8 – Advanced VAPT: Attack Chain & Full Exploitation Project

## Project Overview
This project was completed as part of the DG Interns Hub Cybersecurity Internship. It focuses on practical web application security testing using a local OWASP Juice Shop lab and Burp Suite.

## Objectives
- Identify and document application security weaknesses.
- Inspect HTTP requests and responses.
- Assess observed behavior and potential security impact.
- Map findings to relevant security risks.
- Recommend remediation and retesting steps.

## Lab Environment
- **Target:** OWASP Juice Shop (local lab)
- **Testing tool:** Burp Suite
- **Scope:** Authorized testing of the locally hosted application

## Key Findings

### F-01: SQL Error Disclosure in Product Search
A malformed product-search input caused the application to return a database error and stack-trace details. This demonstrated error disclosure and indicated potentially unsafe query handling. Successful SQL injection or database extraction was not demonstrated.

**Recommended remediation:** Use parameterized queries, return generic client-facing errors, and retain detailed diagnostics only in secure server-side logs.

### F-02: Admin Role Assignment During Registration
During registration testing, the application accepted a client-supplied `admin` role. The local lab confirmed the Admin Registration challenge. Access to protected administrative operations was not independently demonstrated.

**Recommended remediation:** Assign roles on the server, reject or ignore client-supplied privilege fields, and enforce authorization checks on protected operations.

## Evidence and Documentation
This project includes:
- Attack-surface and route inventory notes
- Burp Suite request/response screenshots
- Attack-chain analysis
- Finding reports and risk assessment
- Security test matrix
- Remediation and retest plan
- Final technical report and presentation

## Remediation Status
The remediation and retesting activities are documented as recommendations and planned follow-up work. They should not be considered complete until the fixes are implemented and verified.

## Learning Outcome
This project provided practical experience in web application testing, HTTP traffic analysis, evidence collection, vulnerability documentation, risk assessment, and remediation planning.

**Note:** Testing was conducted against a local intentionally vulnerable training application for educational purposes.
