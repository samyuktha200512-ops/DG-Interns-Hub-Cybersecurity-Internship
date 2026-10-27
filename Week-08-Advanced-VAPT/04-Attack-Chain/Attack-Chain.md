
# Week 8 — Attack-Chain Analysis

## 1. Objective

Document the sequence of security tests performed against the local OWASP Juice Shop application and identify observed behavior, potential impact, and unverified exploitation paths.

## 2. Attack-Chain Overview

```text
Local OWASP Juice Shop
          |
          v
Application Reconnaissance
          |
          v
Authentication Testing
          |
          +---- Invalid login --> HTTP 401
          |
          +---- Successful login --> HTTP 200
          |
          v
Session Behavior Testing
          |
          +---- Authenticated whoami --> HTTP 200
          |
          +---- No Cookie header --> Empty user object
          |                          No data exposure demonstrated
          |
          v
Product Search Testing
          |
          +---- Normal input --> HTTP 200
          |
          +---- Apostrophe input --> HTTP 500
          |                         SQLite error and SQL query exposed
          |
          v
Finding F-01
SQL Error Disclosure in Product Search
          |
          v
Further exploitability verification required
          |
          v
Remediation and retesting
```

## 3. Separate F-02 Registration Test

Separately, a registration request to `POST /api/Users/` included the client-supplied field `role: admin`. The local lab returned HTTP 201 with the role set to `admin`, and the Admin Registration challenge showed success. This is a separate finding (F-02), not a demonstrated continuation of F-01. Administrative operations beyond the challenge behavior were not independently tested.

## 4. Attack-Chain Assessment

The tests demonstrated that malformed product-search input causes an SQLite syntax error and exposes internal query details. This is a confirmed error-disclosure observation.

The tests did not demonstrate successful SQL injection, unauthorized data access, authentication bypass, or data modification. These outcomes must not be presented as successful exploits.

## 5. Recommended Remediation

- Use parameterized SQL queries.
- Return generic error messages to clients.
- Keep stack traces and detailed database errors in protected server-side logs.
- Validate and safely process user input.
- Retest normal and special-character searches after remediation.

## 6. Conclusion

The assessment identified an error-disclosure issue in the product-search functionality. Additional controlled testing is required to establish whether the underlying query construction is exploitable. Findings and conclusions are limited to the evidence collected in the local lab.
```


**Remediation / retest status for F-01 and F-02: Pending Verification.** The two findings were observed through separate tests; a combined exploitation chain was not demonstrated.
