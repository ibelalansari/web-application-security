# SQL Injection - Determine Number of Columns

## Lab Information

| Field | Value |
|-------|-------|
| Platform | PortSwigger Web Security Academy |
| Module | SQL Injection |
| Lab | Determine Number of Columns |
| Difficulty | Apprentice |
| Status | ✅ Solved |

---

## Objective

Determine how many columns are returned by the original SQL query using a UNION SELECT attack.

---

## Vulnerability

SQL Injection

Parameter:

```
category
```

HTTP Method

```
GET
```

---

## Testing Workflow

1. Capture request using Burp Proxy.
2. Send request to Repeater.
3. Confirm SQL Injection with a single quote.
4. Verify comment syntax.
5. Test UNION SELECT with increasing NULL values.
6. Find the correct number of columns.

---

## Successful Payload

```sql
' UNION SELECT NULL,NULL,NULL--
```

---

## Result

The application accepted the payload.

Response:

```
HTTP/2 200 OK
```

The query returns **3 columns**.

---

## Impact

Knowing the correct number of columns allows attackers to perform UNION-based SQL Injection and extract data.

---

## Mitigation

- Prepared Statements
- Parameterized Queries
- Input Validation
- Least Privilege Database Accounts

---

## Tools Used

- Burp Suite Professional
- Firefox
- PortSwigger Academy

---

## Status

✅ Lab Solved