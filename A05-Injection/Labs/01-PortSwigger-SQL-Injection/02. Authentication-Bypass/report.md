# Vulnerability Report

## Title

SQL Injection - Determining Number of Columns Using UNION SELECT

---

## Severity

High

---

## CWE

CWE-89

---

## OWASP

A03:2021 Injection

---

## Description

The application allows SQL Injection through the category parameter.

An attacker can enumerate the number of columns returned by the SQL query using UNION SELECT.

This information can later be used to extract database information.

---

## Affected Parameter

category

---

## Proof of Concept

Successful Payload

```sql
' UNION SELECT NULL,NULL,NULL--
```

---

## Response

HTTP/2 200 OK

---

## Risk

Database Enumeration

Information Disclosure

Facilitates Further SQL Injection

---

## Recommendation

- Parameterized Queries
- Prepared Statements
- Input Validation
- Least Privilege Database User

---

## Verification

Successfully reproduced.

Status

✅ Confirmed