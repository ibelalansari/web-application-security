# SQL Injection

SQL Injection (SQLi) is one of the most critical web application security vulnerabilities. It occurs when an application improperly handles user-supplied input, allowing attackers to manipulate SQL queries executed by the backend database.

This section documents hands-on SQL Injection laboratories completed through PortSwigger Web Security Academy, along with practical methodologies, payloads, observations, screenshots, and mitigation techniques.

---

# Objectives

- Understand SQL Injection fundamentals
- Identify SQL Injection vulnerabilities
- Exploit SQL Injection in controlled lab environments
- Retrieve hidden data from databases
- Perform authentication bypass
- Execute UNION-based SQL Injection
- Understand Blind SQL Injection techniques
- Learn secure mitigation strategies

---

# Learning Topics

- Hidden Data Retrieval
- Authentication Bypass
- UNION Attacks
- Blind SQL Injection (Boolean)
- Blind SQL Injection (Time-Based)
- Error-Based SQL Injection
- Out-of-Band SQL Injection
- Second-Order SQL Injection
- SQL Filter Bypass
- WAF Bypass Techniques

---

# Directory Structure

```text
SQL-Injection
│
├── README.md
│
├── 01. Hidden-Data-Retrieval
├── 02. Authentication-Bypass
├── 03. UNION-Attack
├── 04. Blind-Boolean
├── 05. Blind-Time-Based
├── 06. Error-Based
├── 07. Out-of-Band
├── 08. Second-Order
├── 09. Filter-Bypass
├── 10. WAF-Bypass
└── 11. Cheat-Sheet
```

---

# Tools Used

- Burp Suite Professional
- PortSwigger Web Security Academy
- Firefox Developer Edition
- Kali Linux
- SQLMap (Learning & Validation)
- Browser Developer Tools

---

# Documentation Standard

Each lab includes:

- Lab Objective
- Vulnerability Overview
- Methodology
- Payloads Used
- Burp Suite Requests
- Screenshots
- Findings
- Mitigation
- References

---

# Lab Progress

| Category | Status |
|----------|--------|
| Hidden Data Retrieval | ✅ |
| Authentication Bypass | ✅ |
| UNION Attack | ✅ |
| Blind SQL Injection | ⏳ |
| Error-Based SQL Injection | ⏳ |
| Out-of-Band SQL Injection | ⏳ |
| Second-Order SQL Injection | ⏳ |
| Filter Bypass | ⏳ |
| WAF Bypass | ⏳ |

---

# Learning Resources

- PortSwigger Web Security Academy
- OWASP Web Security Testing Guide
- OWASP Top 10
- PayloadsAllTheThings
- HackTricks

---

# Disclaimer

All exercises documented in this repository were performed in authorized laboratory environments for educational and research purposes only. No unauthorized testing has been conducted against third-party systems.