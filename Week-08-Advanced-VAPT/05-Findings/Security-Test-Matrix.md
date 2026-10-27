# Week 8 — Security Test Matrix

## 1. Purpose

This matrix summarizes the security tests performed against the local OWASP Juice Shop lab, their observed results, and the current assessment status.

## 2. Test Results

| Test ID | Security Test | Observed Result | Assessment |
|---|---|---|---|
| T-01 | Invalid login credentials | HTTP 401 Unauthorized | Completed; expected behavior observed |
| T-02 | Successful login | HTTP 200 OK with authentication data | Completed |
| T-03 | Authenticated `whoami` request | HTTP 200 OK | Completed |
| T-04 | `whoami` request without Cookie header | HTTP 200 OK with an empty user object | No user-data exposure demonstrated |
| T-05 | Normal product search (`test`) | HTTP 200 OK | Baseline established |
| T-06 | Product search with apostrophe (`test'`) | HTTP 500 with SQLite error, stack information, and SQL query exposed | Finding F-01 |
| T-07 | Product search with URL-encoded apostrophe (`test%27`) | Same SQLite syntax error observed | Corroborates Finding F-01 |
| T-08 | Request to `/rest/products` | HTTP 500 with `Unexpected path` message | Invalid endpoint; excluded as a vulnerability finding |
| T-09 | Registration with client-supplied `role: admin` | `POST /api/Users/` returned HTTP 201 Created with `"role":"admin"`; the Admin Registration challenge was solved | Confirmed finding — F-02 |

## 3. Key Findings

### F-01 — SQL Error Disclosure in Product Search

The product-search endpoint returned an SQLite syntax error and internal query details when an apostrophe was included in the search input. Normal input returned HTTP 200, while the modified input returned HTTP 500.

This indicates error disclosure and potentially unsafe SQL query construction. Exploitable SQL injection, unauthorized data access, and data modification have not been confirmed.

### F-02 — Admin Role Assignment During Registration

During registration testing, the `POST /api/Users/` endpoint accepted a client-supplied `role` value of `admin` and returned HTTP 201 Created with the new account's role set to `admin`. The OWASP Juice Shop interface subsequently confirmed that the **Admin Registration** challenge was solved.

This confirms the vulnerable role-assignment behavior in the intentionally vulnerable lab. The authenticated account verification identified the newly created account, but the `whoami` response did not itself include a role field. Administrative operations beyond the challenge behavior were not independently tested.

## 4. Evidence

Evidence screenshots are stored in:

`03-Burp-Evidence/`

Relevant evidence for F-01 includes:

- `E14-Product-Search-Special-Input.png`
- `E15-Product-Search-Normal-Input.png`

Relevant evidence for F-02 includes:

- Registration request and response showing `"role":"admin"`
- `F-01-Authenticated-Account-Verification.png`
- `F-02-Admin-Registration-Challenge-Solved.png`

Verify that all filenames match the actual saved screenshots before submission. Redact authentication tokens, session cookies, passwords, and other sensitive values.

## 5. Limitations

- All tests were performed against a local OWASP Juice Shop lab.
- The `/rest/products` route was not recognized by the application and was excluded from vulnerability findings.
- The cookie-free `whoami` request did not demonstrate user-data exposure.
- SQL injection exploitability, unauthorized data access, and data modification have not been established.
- The Admin Registration challenge confirmed acceptance of a client-supplied administrator role. Other administrative capabilities were not independently tested.
- Severity ratings should be finalized using the project's risk-rating criteria.

## 6. Next Steps

1. Verify all evidence filenames and redact sensitive values.
2. Assess the severity of F-01 and F-02 using the project's risk-rating criteria.
3. Recommend parameterized SQL queries and safe error handling for F-01.
4. Recommend server-controlled role assignment and server-side authorization checks for F-02.
5. Define remediation and retesting criteria for both findings.
6. Include only verified results and clearly stated limitations in the final report.

## Remediation status
F-01 and F-02 remediation and retesting are **Pending Verification**. No successful fix or retest is claimed. See `../06-Remediation/Remediation-Retest-Plan.md` for criteria and blank/not-yet-tested result fields.
