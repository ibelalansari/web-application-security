# 🔐 IDOR — User ID Controlled by Request Parameter

### PortSwigger Web Security Academy · A01 — Broken Access Control

---

## 📌 Overview

This lab demonstrates an **Insecure Direct Object Reference (IDOR)** vulnerability caused by insufficient server-side authorization.

The application uses a client-controlled `id` parameter to identify user accounts. By modifying this parameter while maintaining the same authenticated session, another user's account information can be accessed.

This represents **horizontal privilege escalation** caused by broken object-level authorization.

---

## 🧪 Lab Information

| Field | Details |
|---|---|
| **Platform** | PortSwigger Web Security Academy |
| **Lab** | User ID controlled by request parameter |
| **Vulnerability** | IDOR / Broken Object-Level Authorization |
| **OWASP** | A01 — Broken Access Control |
| **Difficulty** | Apprentice |
| **Tool** | Burp Suite Professional |
| **Authentication** | Authenticated Session |
| **Status** | ✅ Solved |

---

## 🔎 Methodology

1. Authenticate as the `wiener` user.
2. Capture the account request using Burp Suite.
3. Identify the user-controlled `id` parameter.
4. Send the request to Burp Repeater.
5. Change `id=wiener` to `id=carlos`.
6. Keep the same authenticated session.
7. Analyze the server response.
8. Confirm unauthorized access to the `carlos` account.

---

## 🛠️ Step 1 — Identify the Object Reference

The legitimate request was:

```http
GET /my-account?id=wiener HTTP/2
```

<p align="center">
  <img src="./screenshots/01-burp-http-history-wiener-request.png" alt="Burp Suite HTTP History - Wiener Request" width="900">
</p>

The `id` parameter was identified as the user-controlled object reference.

---

## 🛠️ Step 2 — Test with Burp Repeater

The request was sent to Burp Repeater for controlled manipulation.

```http
GET /my-account?id=wiener HTTP/2
```

<p align="center">
  <img src="./screenshots/02-repeater-wiener-request.png" alt="Burp Suite Repeater - Wiener Request" width="900">
</p>

---

## 🔄 Step 3 — Manipulate the ID

The object identifier was changed:

```text
wiener → carlos
```

Modified request:

```http
GET /my-account?id=carlos HTTP/2
```

The authentication session remained unchanged.

---

## 🔎 Step 4 — Validate Unauthorized Access

The modified request returned the `carlos` user's account information, including an API key.

<p align="center">
  <img src="./screenshots/03-repeater-carlos-response-api-key.png" alt="Unauthorized Carlos Account Response" width="900">
</p>

This confirms that the application failed to enforce proper object-level authorization.

---

## ✅ Lab Completion

The vulnerability was successfully reproduced and the PortSwigger lab was completed.

<p align="center">
  <img src="./screenshots/04-lab-solved.png" alt="PortSwigger Lab Solved" width="900">
</p>

---

## ⚠️ Security Impact

An authenticated attacker may be able to access other users' account information by modifying the object identifier.

Potential impact:

- Unauthorized data access
- Sensitive information disclosure
- API key exposure
- Horizontal privilege escalation
- Potential account compromise

---

## 🛡️ Remediation

The application should enforce **server-side authorization checks** for every object access.

Recommended controls:

- Verify object ownership or access permissions.
- Never trust client-controlled identifiers for authorization.
- Apply authorization consistently across all relevant endpoints.
- Return an appropriate authorization error for unauthorized access.
- Use indirect/opaque identifiers as an additional defense, not as a replacement for authorization.

---

## 🏁 Conclusion

This lab demonstrates an **IDOR vulnerability resulting from broken object-level authorization**.

The key security principle is:

> **Authentication determines who you are; authorization determines what you are allowed to access.**

Every user-controlled object reference must be validated against the permissions of the authenticated user.