# F-02: Admin Role Assignment During Registration

## 1. Finding Summary

| Field | Details |
|---|---|
| Finding ID | F-02 |
| Title | Admin Role Assignment During Registration |
| Target | Local OWASP Juice Shop |
| Endpoint | `POST /api/Users/` |
| Category | Broken Access Control / Improper Attribute Assignment |
| Status | Confirmed in the intentionally vulnerable lab |
| Severity | High potential impact; final rating subject to the project's rubric |

## 2. Description

During testing, the registration endpoint accepted a client-supplied `role` field with the value `admin`. The server returned `201 Created` and included `"role":"admin"` in the newly created account's response.

The OWASP Juice Shop webpage subsequently displayed a success message confirming completion of the **Admin Registration** challenge. This demonstrates that the application accepted the administrator-role assignment through the registration workflow.

## 3. Evidence and Observed Results

- The registration request included the additional field `"role":"admin"`.
- The server returned HTTP `201 Created`.
- The response identified the newly created account as ID `26` and returned its role as `admin`.
- An authenticated `GET /rest/user/whoami` request returned HTTP `200 OK` and identified account ID `26`.
- The application displayed the Admin Registration challenge-solved confirmation.

Evidence files:

1. Registration request and response showing the assigned role.
2. `F-01-Authenticated-Account-Verification.png`
3. `F-02-Admin-Registration-Challenge-Solved.png`

## 4. Security Impact

If a production application permits an unauthenticated user to assign themselves an administrator role during registration, an attacker may be able to obtain elevated privileges without authorization. Depending on the application's administrative controls, this could expose sensitive information or allow unauthorized changes.

The challenge-solved confirmation establishes the vulnerable registration behavior in this lab. The exact administrative actions available to the account were not independently tested and should not be claimed as demonstrated.

## 5. Likely Root Cause

The registration process appears to accept a privileged role from client-controlled input rather than enforcing the permitted role on the server. The underlying implementation should be reviewed to confirm the precise cause.

## 6. Recommended Remediation

1. Assign the `customer` role explicitly on the server during public registration.
2. Do not accept privileged fields such as `role`, `isAdmin`, or equivalent attributes from public registration requests.
3. Apply authorization checks on the server for every administrative operation.
4. Add automated tests that attempt to submit privileged fields during registration.
5. Review existing accounts for unauthorized role assignments and audit relevant account-creation events.

**Remediation / retest status:** Pending Verification. No fix or successful retest is claimed.

## 7. Retest Plan

- Register a new test account without a role field and verify that it receives only the standard customer role.
- Repeat registration with a client-supplied `role: admin` field and verify that the server ignores or rejects the field and does not grant administrative privileges.
- Verify that administrative operations remain inaccessible to a normal customer account.
- Confirm that the results are recorded with fresh request and response evidence.

## 8. Conclusion

The local OWASP Juice Shop test confirmed that the registration endpoint accepted a client-supplied administrator role and that the Admin Registration challenge was solved. This is a confirmed role-assignment vulnerability in the lab. Administrative capabilities beyond the challenge behavior remain unverified.