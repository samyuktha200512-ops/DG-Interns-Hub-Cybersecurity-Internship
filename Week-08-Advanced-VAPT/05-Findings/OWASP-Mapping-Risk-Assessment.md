
# Week 8 — OWASP Mapping and Risk Assessment

## 1. Purpose

This document maps the observed test results to relevant security concepts and records their provisional risk levels. Mapping does not imply that a vulnerability has been fully confirmed.

## 2. OWASP Mapping

| Finding / Test | Relevant Security Category | Reason | Assessment Status |
|---|---|---|---|
| F-01: SQL Error Disclosure in Product Search | OWASP Top 10 2021 A05 — Security Misconfiguration (provisional mapping) | Detailed database errors and stack information are returned to the client. | Error disclosure observed |
| F-01: Potential unsafe SQL query construction | OWASP Top 10 2021 A03 — Injection (investigation lead only) | The generated query breaks when an apostrophe is included in the input. | Exploitability unconfirmed |
| Invalid login test | Authentication testing | Invalid credentials returned HTTP 401. | No vulnerability demonstrated |
| Cookie-free `whoami` test | Access-control testing | An empty user object was returned; no user-data exposure was demonstrated. | No vulnerability demonstrated |

## 3. Provisional Risk Assessment

| Finding | Likelihood | Impact | Provisional Risk | Justification |
|---|---|---|---|---|
| F-01: SQL Error Disclosure | Medium (provisional) | Low to Medium (provisional) | Medium (provisional) | Internal database details are disclosed, but unauthorized data access or query manipulation has not been demonstrated. |
| F-02: Admin Role Assignment | High potential impact (provisional) | High potential impact (provisional) | High (provisional; validate with rubric) | Client-supplied admin role was accepted in the lab; protected administrative operations were not independently tested. |

The risk rating is preliminary and should be adjusted according to the assessment methodology and further evidence.

## 4. Recommended Remediation

1. Replace dynamically concatenated SQL with parameterized queries.
2. Return generic error messages to users.
3. Log detailed database errors securely on the server.
4. Verify that special characters are processed as data.
5. Retest normal and malformed search inputs after remediation.

## 5. Retesting Criteria

- Normal product searches continue to work.
- Special-character input does not expose SQL statements or stack traces.
- Database queries use parameter binding.
- Errors are handled consistently without leaking internal implementation details.

## 6. Assessment Limitation

The current evidence confirms SQL error disclosure but does not establish exploitable SQL injection. No unauthorized data retrieval or modification has been demonstrated.


**Remediation / retest status:** F-01 and F-02 are Pending Verification. Do not describe either as fixed or successfully retested until new evidence supports closure.
