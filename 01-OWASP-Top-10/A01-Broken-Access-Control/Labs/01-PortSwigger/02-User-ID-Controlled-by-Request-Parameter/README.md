# IDOR — User ID Controlled by Request Parameter

## Overview

This lab demonstrates an **Insecure Direct Object Reference (IDOR)** vulnerability caused by insufficient server-side authorization checks.

The application uses a user-controlled request parameter to determine which account information is returned. By modifying this parameter while maintaining the same authenticated session, it is possible to access another user's account information.

---

## Lab Information

| Field | Details |
|---|---|
| Platform | PortSwigger Web Security Academy |
| Vulnerability | Insecure Direct Object Reference (IDOR) |
| Security Category | Broken Access Control |
| Lab | User ID controlled by request parameter |
| Difficulty | Apprentice |
| Tool | Burp Suite Professional |
| Testing Method | Manual request manipulation |
| Status | Solved |

---

## Objective

Access another user's account information by manipulating the user-controlled `id` request parameter.

---

## Vulnerability Description

The application determines the requested account using a value supplied by the client:

```http
GET /my-account?id=wiener HTTP/2