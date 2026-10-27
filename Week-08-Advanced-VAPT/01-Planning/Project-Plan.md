# Week 8 — Advanced VAPT Project Plan

## 1. Project Overview

| Item | Details |
|---|---|
| Internship | DG Interns Hub Cybersecurity Internship |
| Week | 8 |
| Project | Advanced VAPT — Attack Chain & Full Exploitation Project |
| Target Application | OWASP Juice Shop |
| Testing Environment | Local authorized lab |
| Deadline | 28 October 2026 |

## 2. Objective

The objective of this project is to assess the security of the intentionally vulnerable OWASP Juice Shop application in a controlled local environment. The assessment focuses on identifying weaknesses, validating security observations using practical evidence, documenting potential impact, and recommending suitable remediation measures.

## 3. Scope and Authorization

### In Scope
- Local OWASP Juice Shop application.
- Application routes and exposed functionality.
- Authentication and session behavior.
- Input validation and error handling.
- Registration and role-assignment behavior.
- Relevant HTTP requests and responses captured using Burp Suite.
- Remediation recommendations and retesting criteria.

### Out of Scope
- Public or third-party systems.
- Systems without explicit authorization.
- Denial-of-service testing.
- Destructive actions or unnecessary data modification.
- Claims of impact that have not been demonstrated by evidence.

All testing is intended for the local training application.

## 4. Lab Environment and Tools

| Component | Purpose |
|---|---|
| Kali Linux | Security testing environment |
| OWASP Juice Shop | Intentionally vulnerable target application |
| Burp Suite | HTTP request and response inspection and replay |
| Web browser | Application interaction and verification |
| Nmap, if used | Network and service discovery |
| Markdown and screenshot tools | Documentation and evidence management |

The report will include only tools and activities supported by the actual project evidence.

## 5. Testing Methodology

The assessment follows these phases:

1. **Planning:** Define the objective, scope, authorization, and testing boundaries.
2. **Attack-surface discovery:** Access the local application and identify relevant pages, routes, and functionality.
3. **Request inspection:** Use Burp Suite to observe application requests and responses.
4. **Security testing:** Examine authentication behavior, input handling, registration behavior, and role assignment within the authorized lab.
5. **Evidence collection:** Save genuine screenshots, relevant responses, and test results.
6. **Finding validation:** Compare observed behavior with expected secure behavior and distinguish confirmed findings from unverified possibilities.
7. **Risk assessment:** Explain potential impact and assign severity based on available evidence.
8. **Remediation planning:** Recommend fixes and define criteria for retesting.
9. **Documentation:** Prepare the technical report, presentation, and final submission package.

## 6. Evidence Collection Plan

Evidence should be saved in the relevant project folders:

- `02-Attack-Surface/` — initial access, discovered pages, and route inventory.
- `03-Burp-Evidence/` — relevant HTTP requests, responses, and security-test screenshots.
- `04-Attack-Chain/` — the documented sequence of testing activities.
- `05-Findings/` — findings, test matrix, risk assessment, and supporting references.
- `06-Remediation/` — recommendations and retest plan.
- `07-Report/` — technical report and evidence index.
- `08-Presentation/` — final presentation.
- `09-Submission/` — final submission package, if required.

Screenshots must represent actual test results. Sensitive values such as passwords, tokens, and session cookies must be redacted before sharing.

## 7. Reporting Principles

- Record the actual observed result for each test.
- Distinguish confirmed behavior from suspected vulnerabilities.
- Do not claim successful exploitation unless the evidence demonstrates it.
- Link each finding to relevant evidence.
- Provide practical remediation and retesting recommendations.
- Keep the report clear, concise, and consistent with the original project files.

## 8. Project Completion Criteria

The project is considered ready for submission when:

- Relevant practical evidence has been organized.
- Security findings and test results are documented accurately.
- Risk assessments and remediation recommendations are included.
- The technical report and presentation are complete and checked.
- Sensitive information is redacted.
- The final files are organized for submission.

## 9. Ethical Considerations

This project is conducted for educational purposes using an intentionally vulnerable application in a controlled local environment. Testing is restricted to the authorized scope. Findings are documented responsibly, and conclusions are limited to what was demonstrated during the assessment.

---

**Document purpose:** This plan records the intended scope, methodology, and evidence-management approach for the Week 8 assessment. Actual results and conclusions are documented separately in the test matrix, findings, and technical report.