# Week 8 — Remediation and Retesting Plan

## 1. Objective and status
This plan defines corrective actions and retest criteria for both findings. **Remediation and retesting status for F-01 and F-02: Pending Verification.** No fix or successful retest is claimed. Actual results remain `Not yet tested` until a retest is performed and supported by fresh evidence.

## 2. F-01 — SQL Error Disclosure in Product Search
**Endpoint:** `GET /rest/products/search?q=...`
**Observed baseline:** normal input returned HTTP 200. Apostrophe and URL-encoded apostrophe inputs returned HTTP 500 and disclosed SQLite/query/stack details. This is confirmed error disclosure; successful SQL injection or database extraction was not demonstrated.

### Remediation actions
- **Parameterized queries:** use prepared statements / parameter binding; do not build SQL statements by concatenating user-controlled search terms.
- **Safe error handling:** return generic client-facing errors; keep detailed SQL errors and stack traces in access-controlled server-side logs.
- Review related query paths and validate search input without relying on validation as a substitute for parameterization.
- **Regression testing:** test normal searches and special-character inputs to confirm expected search behavior without database-error disclosure.

### Retest table
| Test ID | Criteria | Actual result | Status |
|---|---|---|---|
| F01-RT-01 | Normal search (`test`) returns expected results without regression. | Not yet tested | Pending Verification |
| F01-RT-02 | Apostrophe input (`test'`) does not disclose SQL errors, query text, or stack traces. | Not yet tested | Pending Verification |
| F01-RT-03 | URL-encoded apostrophe (`test%27`) is handled safely without internal error disclosure. | Not yet tested | Pending Verification |
| F01-RT-04 | Implementation uses parameter binding for the search term. | Not yet tested | Pending Verification |

## 3. F-02 — Admin Role Assignment During Registration
**Endpoint:** `POST /api/Users/`
**Observed behavior:** a request containing `role: admin` received HTTP 201 Created with `role: admin`, and the Admin Registration challenge displayed a success confirmation in the local lab. Protected administrative operations were not independently verified.

### Remediation actions
- **Server-side role enforcement:** assign the default customer role on the server during public registration.
- **Client-supplied privilege fields:** reject or ignore client-supplied fields such as `role: admin`, `isAdmin`, or equivalent privilege attributes. Never trust the role supplied by the client.
- **Authorization testing:** verify customer accounts cannot access protected administrative operations and ensure authorization is enforced server-side on every administrative endpoint.
- Review existing accounts for unauthorized role assignments and audit relevant registration events, where appropriate.

### Retest table
| Test ID | Criteria | Actual result | Status |
|---|---|---|---|
| F02-RT-01 | Public registration without a role field creates a customer account. | Not yet tested | Pending Verification |
| F02-RT-02 | Registration with `role: admin` is rejected or ignored; no administrator role is granted. | Not yet tested | Pending Verification |
| F02-RT-03 | A customer account is denied access to protected administrative operations. | Not yet tested | Pending Verification |
| F02-RT-04 | Server-side authorization checks are present and enforced for administrative operations. | Not yet tested | Pending Verification |

## 4. Retest evidence and closure rules
Record the retest date, environment/build, exact request/response, result, and evidence filename for each test. Keep status **Pending Verification** until genuine retest evidence is captured. Only mark a test passed after the acceptance criteria are met; if any criterion fails, document the observed result and keep the finding open.

## 5. Overall status
- **F-01:** Pending Verification — remediation and retesting not yet demonstrated.
- **F-02:** Pending Verification — remediation and retesting not yet demonstrated.
