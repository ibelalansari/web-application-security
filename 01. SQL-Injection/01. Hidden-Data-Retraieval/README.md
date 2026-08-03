# SQL Injection Vulnerability in WHERE Clause Allowing Retrieval of Hidden Data

## Overview

This lab demonstrates a classic SQL Injection vulnerability in the `WHERE` clause of an SQL query. By manipulating user-controlled input, an attacker can modify the application's SQL query to retrieve hidden records that should not normally be accessible.

The objective of this lab is to identify the injection point, exploit the vulnerability, and retrieve all hidden products from the database.

---

# Lab Information

| Item | Details |
|------|---------|
| Platform | PortSwigger Web Security Academy |
| Category | SQL Injection |
| Difficulty | Apprentice |
| Lab | SQL injection vulnerability in WHERE clause allowing retrieval of hidden data |
| Status | ✅ Solved |

---

# Objective

Retrieve hidden products by exploiting an SQL Injection vulnerability in the application's `WHERE` clause.

---

# Vulnerability Overview

The application constructs an SQL query using unsanitized user input received from the `category` parameter.

Original query:

```sql
SELECT * FROM products
WHERE category='Gifts'
AND released=1;
```

Because user input is directly concatenated into the SQL statement, an attacker can inject additional SQL syntax.

---

# Methodology

1. Intercept the request using Burp Suite Professional.
2. Identify the vulnerable `category` parameter.
3. Inject an SQL payload to terminate the original query.
4. Remove the application's filtering condition.
5. Retrieve all available products, including hidden entries.

---

# Payload Used

```sql
' OR 1=1--
```

Example request:

```http
GET /filter?category=Gifts'+OR+1=1--
```

---

# Tools Used

- Burp Suite Professional
- Firefox Developer Edition
- PortSwigger Web Security Academy

---

# Screenshots

Store screenshots inside:

```
screenshots/
├── 01-homepage.png
├── 02-burp-request.png
├── 03-payload.png
└── 04-lab-solved.png
```

---

# Findings

- SQL Injection vulnerability confirmed.
- User input was not properly sanitized.
- Hidden products became accessible.
- The application trusted user-controlled input.

---

# Impact

An attacker could potentially:

- Retrieve unauthorized data
- Bypass application restrictions
- Enumerate database contents
- Prepare for further SQL Injection attacks

---

# Mitigation

- Use parameterized queries (Prepared Statements).
- Avoid dynamic SQL query construction.
- Implement server-side input validation.
- Apply the principle of least privilege to database accounts.
- Perform regular security testing.

---

# References

- PortSwigger Web Security Academy
- OWASP SQL Injection Prevention Cheat Sheet
- OWASP Top 10 – Injection

---

# Disclaimer

This lab was completed in an authorized laboratory environment for educational and research purposes only.