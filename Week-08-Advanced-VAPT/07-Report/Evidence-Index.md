# Week 8 — Evidence Index

## Purpose
This index maps evidence to the actual filenames in the supplied archive. Paths are relative to `Week-08-Advanced-VAPT/`. No screenshots were renamed.

## Evidence register

| Evidence ID | Folder | Exact filename | Description | Test / finding |
|---|---|---|---|---|
| E-01 | `02-Attack-Surface/` | `E01-Juice-Shop-Initial-Access.png` | E01 Juice Shop Initial Access | Attack-surface / reconnaissance |
| E-02 | `02-Attack-Surface/` | `E02-Login-Page.png` | E02 Login Page | Authentication / T-01–T-02 |
| E-03 | `02-Attack-Surface/` | `E03-Registration-Page.png` | E03 Registration Page | F-02 / T-09 |
| E-04 | `03-Burp-Evidence/` | `E01-Burp-Browser-Access.png` | E01 Burp Browser Access | Attack-surface / reconnaissance |
| E-05 | `03-Burp-Evidence/` | `E02-Burp-Site-Map.png` | E02 Burp Site Map | Attack-surface / reconnaissance |
| E-06 | `03-Burp-Evidence/` | `E03-Security-Questions-API.png` | E03 Security Questions API | Attack-surface / reconnaissance |
| E-07 | `03-Burp-Evidence/` | `E04-Quantity-API.png` | E04 Quantity API | Attack-surface / reconnaissance |
| E-08 | `03-Burp-Evidence/` | `E05-Login-Request.png` | E05 Login Request | Authentication / T-01–T-02 |
| E-09 | `03-Burp-Evidence/` | `E06-Login-Response.png` | E06 Login Response | Authentication / T-01–T-02 |
| E-10 | `03-Burp-Evidence/` | `E07-Login-Replay-Baseline.png` | E07 Login Replay Baseline | Authentication / T-01–T-02 |
| E-11 | `03-Burp-Evidence/` | `E08-Login-Invalid-Credentials-Comparison.png` | E08 Login Invalid Credentials Comparison | Authentication / T-01–T-02 |
| E-12 | `03-Burp-Evidence/` | `E09-Registration-Request-Response.png` | E09 Registration Request Response | F-02 / T-09 |
| E-13 | `03-Burp-Evidence/` | `E10-Login-Success-Response.png` | E10 Login Success Response | Authentication / T-01–T-02 |
| E-14 | `03-Burp-Evidence/` | `E11-Whoami-Authenticated-Baseline.png` | E11 Whoami Authenticated Baseline | Application access / reconnaissance |
| E-15 | `03-Burp-Evidence/` | `E12-Whoami-Unauthenticated-Test.png` | E12 Whoami Unauthenticated Test | Application access / reconnaissance |
| E-16 | `03-Burp-Evidence/` | `E13-Product-Search-Baseline.png` | E13 Product Search Baseline | F-01 / T-05–T-07 |
| E-17 | `03-Burp-Evidence/` | `E14-Product-Search-Special-Input.png` | E14 Product Search Special Input | F-01 / T-05–T-07 |
| E-18 | `03-Burp-Evidence/` | `E15-Product-Search-Normal-Input.png` | E15 Product Search Normal Input | F-01 / T-05–T-07 |
| E-19 | `03-Burp-Evidence/` | `F-01-Authenticated-Account-Verification.png` | F 01 Authenticated Account Verification | F-01 / T-05–T-07 |
| E-20 | `03-Burp-Evidence/` | `F-02-Admin-Registration-Challenge-Solved.png` | F 02 Admin Registration Challenge Solved | F-02 / T-09 |
| E-21 | `05-Findings/` | `F-02-Admin-Role-Registration.png` | F 02 Admin Role Registration | F-02 / T-09 |

## Supporting documents

- `01-Planning/Project-Plan.md` — scope, objectives, and methodology.
- `02-Attack-Surface/04-Route-Inventory.txt` — observed pages and target URL.
- `04-Attack-Chain/Attack-Chain.md` — test sequence and limitations.
- `05-Findings/F-01-SQL-Error-Disclosure-Product-Search.md` — F-01.
- `05-Findings/F-02-Admin-Role-Assignment.md` — F-02.
- `05-Findings/Security-Test-Matrix.md` — test outcomes.
- `05-Findings/OWASP-Mapping-Risk-Assessment.md` — mapping and provisional risk.
- `06-Remediation/Remediation-Retest-Plan.md` — corrective actions and pending retest plan.

## Evidence handling
- Check screenshots for passwords, access tokens, cookies, or other secrets and redact them before external submission.
- F-01 demonstrates SQL-related error disclosure; SQL injection, data extraction, and data modification were not demonstrated.
- F-02 demonstrates client-supplied administrator-role acceptance and the challenge-success message in the lab. Other administrative operations were not independently verified.
- F-01 and F-02 are separate findings; a combined exploitation chain was not demonstrated.
