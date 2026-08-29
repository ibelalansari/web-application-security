# Learning Notes

## Topic

Hidden Data Retrieval using SQL Injection

---

## What I Learned

This lab demonstrates a SQL Injection vulnerability inside a SQL WHERE clause.

The application only displays products where:

```sql
released = 1
```

By injecting a SQL comment, the remainder of the query is ignored.

---

## Original Query

```sql
SELECT * FROM products
WHERE category='Gifts'
AND released=1;
```

---

## Injected Payload

```sql
'--
```

---

## Final Query

```sql
SELECT * FROM products
WHERE category='Gifts'--'
AND released=1;
```

The SQL comment (`--`) causes the database to ignore everything after it.

As a result:

- Hidden products become visible.
- Application logic is bypassed.

---

## Key Concepts

- SQL Injection
- WHERE Clause
- SQL Comments
- Application Logic Bypass

---

## Indicators

- More products appear.
- Hidden items become visible.
- HTTP Response remains 200 OK.

---

## Defensive Measures

- Prepared Statements
- Parameterized Queries
- ORM
- Input Validation

---

## Skills Practiced

- Burp Proxy
- Burp Repeater
- HTTP Request Analysis
- SQL Payload Testing