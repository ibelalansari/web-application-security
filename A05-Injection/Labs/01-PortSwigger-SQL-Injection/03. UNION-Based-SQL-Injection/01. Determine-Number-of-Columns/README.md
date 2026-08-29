# 💉 SQL Injection — Determine Number of Columns

### PortSwigger Web Security Academy · A05 — Injection

---

## 🧪 Lab Information

| Field | Value |
|---|---|
| **Platform** | PortSwigger Web Security Academy |
| **Module** | SQL Injection |
| **Lab** | Determine Number of Columns |
| **Difficulty** | Apprentice |
| **Parameter** | `category` |
| **HTTP Method** | GET |
| **Status** | ✅ Solved |

---

## 🎯 Objective

Determine the number of columns returned by the original SQL query using a **UNION SELECT** attack.

---

## 🔎 Vulnerability

The application is vulnerable to **SQL Injection** through the `category` parameter.

The injectable parameter was identified as:

```text
category
```

The objective was to determine the correct number of columns before proceeding with further UNION-based SQL Injection testing.

---

## 🧭 Testing Workflow

1. Capture the request using Burp Suite Proxy.
2. Send the request to Burp Repeater.
3. Test a single quote to identify SQL Injection behavior.
4. Test SQL comment syntax.
5. Test `UNION SELECT` with increasing numbers of `NULL` values.
6. Identify the correct number of columns.
7. Verify the successful response.

---

## 🛠️ Step 1 — Capture the Request

The HTTP request was captured using **Burp Suite Proxy / HTTP History**.

<p align="center">
  <img src="./screenshots/01-http-history.png" alt="Burp Suite HTTP History" width="900">
</p>

---

## 🛠️ Step 2 — Send Request to Repeater

The captured request was sent to **Burp Suite Repeater** for controlled SQL Injection testing.

<p align="center">
  <img src="./screenshots/02-send-to-repeater.png" alt="Send Request to Burp Repeater" width="900">
</p>

The original request was reviewed before injecting SQL syntax.

<p align="center">
  <img src="./screenshots/03-original-request.png" alt="Original HTTP Request" width="900">
</p>

---

## 🔬 Step 3 — Confirm SQL Injection

A single quote was introduced into the `category` parameter to observe the application's behavior.

The resulting error indicated that user input was being interpreted within the SQL query.

<p align="center">
  <img src="./screenshots/04-single-quote-error.png" alt="Single Quote SQL Injection Error" width="900">
</p>

The application also produced an internal server error when the SQL syntax was malformed.

<p align="center">
  <img src="./screenshots/05-render-internal-server-error.png" alt="Internal Server Error During SQL Injection Testing" width="900">
</p>

---

## 🧪 Step 4 — Test UNION SELECT

The SQL comment syntax was tested to determine whether the remainder of the original query could be neutralized.

<p align="center">
  <img src="./screenshots/06-comment-test.png" alt="SQL Comment Syntax Test" width="900">
</p>

The number of columns was then tested using increasing numbers of `NULL` values:

```sql
' UNION SELECT NULL--
' UNION SELECT NULL,NULL--
' UNION SELECT NULL,NULL,NULL--
```

The two-column UNION attempt failed:

<p align="center">
  <img src="./screenshots/07-union-select-2-columns-error.png" alt="Two Column UNION SELECT Error" width="900">
</p>

The three-column UNION attempt was successful:

```sql
' UNION SELECT NULL,NULL,NULL--
```

<p align="center">
  <img src="./screenshots/08-union-select-3-columns-success.png" alt="Three Column UNION SELECT Success" width="900">
</p>

---

## ✅ Result

The successful payload confirmed that the original SQL query returns **3 columns**.

```http
HTTP/2 200 OK
```

The PortSwigger lab was successfully completed.

<p align="center">
  <img src="./screenshots/09-lab-solved.png" alt="PortSwigger Lab Solved" width="900">
</p>

---

## ⚠️ Impact

Determining the correct number of columns is a fundamental step in a UNION-based SQL Injection attack.

Once the column count is known, an attacker may potentially use UNION queries to retrieve information from the database, depending on the application's SQL context and database privileges.

---

## 🛡️ Mitigation

Recommended defenses include:

- Use **prepared statements / parameterized queries**
- Avoid concatenating user input into SQL statements
- Use secure ORM/database access methods
- Apply appropriate input validation
- Use least-privileged database accounts
- Perform regular SQL Injection security testing

---

## 🧠 Skills Demonstrated

- SQL Injection Testing
- UNION-Based SQL Injection
- Column Count Enumeration
- HTTP Request Analysis
- Burp Suite Proxy
- Burp Suite Repeater
- Manual Web Application Security Testing

---

## 🏁 Status

**✅ Successfully Solved**