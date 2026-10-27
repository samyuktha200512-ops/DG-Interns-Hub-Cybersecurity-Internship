# Finding F-01: SQL Error Disclosure in Product Search

**Affected endpoint:** `GET /rest/products/search?q=...`

**Test input:** `test'` and URL-encoded `test%27`

**Expected behavior:** The application should handle special characters safely and return a controlled response without exposing internal database details.

**Observed behavior:** Normal input (`test`) returned HTTP 200. Apostrophe input returned HTTP 500 and exposed an SQLite syntax error, stack information, and the generated SQL query.

**Security impact:** The response reveals internal database implementation details and indicates that malformed search input causes an unhandled database error. Whether this behavior permits SQL injection or unauthorized data access remains unverified.

**Severity:** Provisional Medium; confirm using the organization's risk criteria and additional evidence.

**Recommended remediation:**
1. Replace string-concatenated SQL with parameterized queries.
2. Handle special characters as data rather than SQL syntax.
3. Return generic error messages to clients.
4. Keep detailed stack traces and database errors in protected server-side logs.
5. Retest normal and special-character inputs after remediation.

**Retest acceptance criteria:** Search requests are handled without exposing SQL statements, stack traces, or database errors. Valid searches continue to work, and the query uses parameter binding.