# Vulnerability Report

## Title

SQL Injection in WHERE Clause allowing Hidden Data Retrieval

---

## Severity

High

---

## CWE

CWE-89

---

## OWASP

A03:2021 - Injection

---

## Description

The application fails to properly sanitize user-controlled input before incorporating it into SQL queries.

An attacker can manipulate the SQL statement to bypass filtering conditions.

---

## Affected Parameter

category

---

## Proof of Concept

Request

```
GET /filter?category=Gifts'--
```

Payload

```sql
'--
```

---

## Result

Hidden products are displayed.

---

## Risk

- Unauthorized Data Disclosure
- Business Logic Bypass

---

## Recommendation

- Use Prepared Statements
- Use Parameterized Queries
- Validate Input
- Escape User Input
- Apply Least Privilege Database Accounts

---

## Verification

Successfully reproduced.

Status:

✅ Confirmed