# SQL Injection Vulnerability in WHERE Clause Allowing Retrieval of Hidden Data

> **PortSwigger Web Security Academy** — SQL Injection Lab Write-up

---

## Overview

This lab demonstrates how a vulnerable SQL query can be manipulated through the `category` parameter to retrieve hidden records from the database.

The application concatenates user input directly into a SQL `WHERE` clause, allowing an attacker to modify the query logic and access data that should remain hidden.

---

## Lab Information

| Field | Value |
|-------|-------|
| Platform | PortSwigger Web Security Academy |
| Category | SQL Injection |
| Technique | WHERE Clause SQL Injection |
| Difficulty | Apprentice |
| Status | ✅ Solved |

---

## Objective

Exploit the vulnerable `category` parameter to retrieve hidden products from the application's database.

---

## Vulnerability

The application builds the SQL query using unsanitized user input.

Original query:

```sql
SELECT * FROM products
WHERE category='Gifts'
AND released=1;
```

Because the input is not properly sanitized, additional SQL syntax can be injected.

---

## Tools Used

- Burp Suite Professional
- Burp Repeater
- Firefox
- PortSwigger Web Security Academy

---

## Methodology

### Step 1 — Capture the Request

Intercept the request using Burp Suite Proxy.

**Screenshot**

![Burp Proxy History](screenshots/01-burp-proxy-history.png)

---

### Step 2 — Send to Burp Repeater

Forward the request to Burp Repeater for manual testing.

**Screenshot**

![Burp Repeater Request](screenshots/02-burp-repeater-request.png)

---

### Step 3 — Observe the Original Response

Review the application's normal response before testing.

**Screenshot**

![Original Response](screenshots/03-burp-repeater-render.png)

---

### Step 4 — Inject the SQL Payload

Inject the following payload into the `category` parameter.

```sql
' OR 1=1--
```

The injected payload causes the SQL query to return all products, including hidden records.

**Screenshot**

![SQL Injection Payload](screenshots/04-sqli-payload.png)

---

### Step 5 — Verify Lab Completion

The application returns all hidden products and the lab is successfully completed.

**Screenshot**

![Lab Solved](screenshots/05-lab-solved.png)

---

## Payload Used

```sql
' OR 1=1--
```

Example request:

```http
GET /filter?category=Gifts'+OR+1=1--
```

---

## Findings

- SQL Injection vulnerability confirmed.
- Unsanitized user input modified the SQL query.
- Hidden products became accessible.
- Business logic restrictions were bypassed.

---

## Impact

An attacker could potentially:

- Access hidden records
- Retrieve unauthorized information
- Bypass application restrictions
- Enumerate sensitive database content

---

## Mitigation

- Use parameterized queries (Prepared Statements).
- Never concatenate user input into SQL queries.
- Validate and sanitize all user input.
- Apply the principle of least privilege.
- Perform regular security testing.

---

## Skills Practiced

- SQL Injection
- WHERE Clause Manipulation
- Burp Suite Proxy
- Burp Repeater
- HTTP Request Analysis
- Manual Web Application Testing

---

## References

- PortSwigger Web Security Academy
- OWASP SQL Injection Prevention Cheat Sheet
- OWASP Web Security Testing Guide (WSTG)
- CWE-89: SQL Injection

---

## Disclaimer

This lab was completed exclusively within the PortSwigger Web Security Academy environment for educational purposes. All testing was performed only on authorized systems.