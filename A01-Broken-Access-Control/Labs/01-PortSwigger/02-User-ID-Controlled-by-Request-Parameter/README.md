# 🔐 IDOR — User ID Controlled by Request Parameter

### PortSwigger Web Security Academy · A01 — Broken Access Control

---

## 📌 Overview

This lab demonstrates an **Insecure Direct Object Reference (IDOR)** vulnerability caused by insufficient server-side authorization controls.

The application uses a client-controlled `id` request parameter to determine which user's account information is returned.

Although the application correctly authenticates the user, it fails to verify whether the authenticated user is authorized to access the requested account.

By modifying the `id` parameter while maintaining the same authenticated session, another user's account information can be accessed.

This is a classic example of **horizontal privilege escalation** caused by broken object-level authorization.

---

## 🎯 Objective

The objective of this lab is to determine whether an authenticated user can access another user's account information by manipulating a user-controlled object identifier.

The assessment focuses on:

- Identifying the account endpoint
- Identifying the object reference
- Capturing the authenticated request
- Establishing a legitimate baseline
- Manipulating the object identifier
- Maintaining the original authentication context
- Analyzing the server response
- Validating unauthorized object access
- Assessing the security impact
- Identifying the root cause
- Recommending remediation
- Defining a retesting strategy

---

## 🧪 Lab Information

| Field | Details |
|---|---|
| **Platform** | PortSwigger Web Security Academy |
| **Lab** | User ID controlled by request parameter |
| **Vulnerability** | Insecure Direct Object Reference (IDOR) |
| **OWASP Category** | A01 — Broken Access Control |
| **Vulnerability Type** | Broken Object-Level Authorization |
| **Difficulty** | Apprentice |
| **Primary Tool** | Burp Suite Professional |
| **Testing Method** | Manual Request Manipulation |
| **Authentication** | Authenticated Session |
| **Affected Functionality** | User Account |
| **Status** | ✅ Solved |

---

# 🔎 Attack Surface Identification

The vulnerable functionality is the authenticated account endpoint:

```http
GET /my-account?id=wiener HTTP/2