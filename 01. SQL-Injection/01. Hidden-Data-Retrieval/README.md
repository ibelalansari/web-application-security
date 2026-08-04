# SQL Injection Vulnerability in WHERE Clause Allowing Retrieval of Hidden Data

> **PortSwigger Web Security Academy** lab demonstrating how an SQL Injection vulnerability in a `WHERE` clause can expose hidden data that should not be accessible to users.

---

## Lab Information

| Field | Value |
|-------|-------|
| Platform | PortSwigger Web Security Academy |
| Category | SQL Injection |
| Technique | SQL Injection in WHERE Clause |
| Difficulty | Apprentice |
| Status | ✅ Solved |

---

## Overview

This lab demonstrates a classic SQL Injection vulnerability caused by insecure handling of user input within the `WHERE` clause of an SQL query.

By manipulating the vulnerable parameter, it is possible to modify the application's SQL logic and retrieve records that were intentionally hidden from users.

This exercise highlights the importance of secure query construction and demonstrates how a seemingly simple injection can compromise application data confidentiality.

---

## Objective

- Identify the SQL Injection vulnerability.
- Manipulate the vulnerable `WHERE` clause.
- Retrieve hidden products from the database.
- Understand the impact of insecure SQL query construction.
- Document the exploitation process.

---

## Tools Used

- Burp Suite Professional
- Burp Repeater
- Firefox
- PortSwigger Web Security Academy

---

# Methodology

## Step 1 — Browse the Application

Navigate to the vulnerable **Gifts** category.

**Screenshot**

![](screenshots/01-homepage.png)

---

## Step 2 — Intercept the HTTP Request

Capture the request using Burp Suite Proxy.

**Screenshot**

![](screenshots/02-burp-request.png)

---

## Step 3 — Inject the SQL Payload

Modify the vulnerable `category` parameter with the following payload:

```sql
' OR 1=1--
```

The injected condition always evaluates to **TRUE**, causing the application to return all products, including hidden entries.

**Screenshot**

![](screenshots/03-payload.png)

---

## Step 4 — Verify Lab Completion

After submitting the payload, the hidden products become visible and the lab is successfully completed.

**Screenshot**

![](screenshots/04-lab-solved.png)

---

# Original SQL Query

```sql
SELECT * FROM products
WHERE category='Gifts'
AND released=1;
```

---

# Payload Used

```sql
' OR 1=1--
```

Example HTTP Request

```http
GET /filter?category=Gifts'+OR+1=1--
```

---

# Findings

- SQL Injection vulnerability confirmed.
- User-controlled input was concatenated directly into the SQL query.
- Hidden products became accessible.
- Application logic was successfully manipulated.
- Input validation and parameterized queries were absent.

---

# Impact

A successful attacker could potentially:

- Retrieve unauthorized information
- Access hidden application content
- Enumerate database records
- Facilitate further SQL Injection attacks
- Compromise application confidentiality

---

# Key Learning

- SQL Injection can alter application logic by modifying the `WHERE` clause.
- A single vulnerable parameter can expose sensitive information.
- Parameterized queries are the most effective defense against SQL Injection.
- Understanding SQL query logic is essential for both attackers and defenders.

---

# Mitigation

- Use parameterized queries (Prepared Statements).
- Never concatenate user input into SQL queries.
- Validate and sanitize all user input.
- Apply the Principle of Least Privilege.
- Suppress detailed SQL error messages.
- Conduct regular application security assessments.

---

# Skills Practiced

- SQL Injection
- WHERE Clause Manipulation
- Burp Suite Proxy
- Burp Repeater
- HTTP Request Analysis
- Manual Web Application Testing

---

# References

- PortSwigger Web Security Academy
- OWASP SQL Injection Prevention Cheat Sheet
- OWASP Web Security Testing Guide (WSTG)
- CWE-89: SQL Injection

---

# Disclaimer

This write-up documents an authorized laboratory exercise completed within the PortSwigger Web Security Academy. All testing was performed exclusively in a controlled environment for educational and research purposes.