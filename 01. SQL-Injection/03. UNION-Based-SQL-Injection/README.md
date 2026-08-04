<p align="center">
  <h1 align="center">UNION-Based SQL Injection</h1>
  <p align="center">
    A collection of PortSwigger Web Security Academy labs demonstrating UNION-based SQL Injection techniques.
  </p>
</p>

---

# Overview

UNION-based SQL Injection is a technique that leverages the SQL `UNION` operator to combine the results of multiple `SELECT` statements into a single response. If an application returns query results directly to users, an attacker may use a vulnerable parameter to retrieve arbitrary data from the underlying database.

These labs demonstrate the process of identifying UNION-compatible queries, discovering injectable columns, and extracting sensitive information from backend database tables.

---

# Objectives

- Understand the SQL `UNION` operator
- Determine the number of returned columns
- Identify columns capable of displaying user-controlled data
- Extract information from database tables
- Practice safe, structured testing methodologies
- Improve web application security assessment skills

---

# Skills Covered

- SQL Injection
- UNION SELECT
- Column Enumeration
- Text Column Identification
- Database Enumeration
- Table Enumeration
- Column Enumeration
- Credential Extraction
- Burp Suite Repeater
- HTTP Request Manipulation

---

# Tools Used

- Burp Suite Professional
- Firefox
- PortSwigger Web Security Academy

---

# Lab Collection

| # | Lab | Status |
|---|-----|--------|
| 01 | Finding Column Containing Text | ✅ Completed |
| 02 | Retrieving Data from Other Tables | ✅ Completed |

---

# Directory Structure

```text
03. UNION-Based-SQL-Injection
│
├── README.md
│
├── Finding-Column-Containing-Text
│   ├── README.md
│   ├── payloads.txt
│   └── screenshots/
│
└── Retrieving-Data-from-Other-Tables
    ├── README.md
    ├── payloads.txt
    └── screenshots/
```

---

# Learning Outcomes

After completing these labs, you should be able to:

- Determine whether a SQL query supports UNION operations
- Identify the correct number of columns
- Locate columns capable of displaying textual data
- Enumerate database tables and columns
- Retrieve data from other tables using UNION SELECT
- Document SQL Injection findings professionally

---

# References

- PortSwigger Web Security Academy
- OWASP Web Security Testing Guide (WSTG)
- OWASP Top 10
- CWE-89: SQL Injection
- MITRE ATT&CK

---

# Disclaimer

All techniques demonstrated in this repository are performed exclusively within authorized laboratory environments provided by PortSwigger Web Security Academy. They are intended solely for educational purposes and authorized security testing.