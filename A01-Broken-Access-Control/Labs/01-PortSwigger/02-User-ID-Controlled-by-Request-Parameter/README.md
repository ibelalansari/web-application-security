# IDOR — User ID Controlled by Request Parameter

## Overview

This lab demonstrates an **Insecure Direct Object Reference (IDOR)** vulnerability caused by insufficient server-side authorization controls.

The application uses a user-controlled `id` request parameter to determine which account information is returned. Because the server does not properly verify whether the authenticated user is authorized to access the requested account, modifying the parameter allows access to another user's account information.

This is a classic **Broken Access Control** scenario where authentication is present, but authorization is insufficient.

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
| Authentication | Authenticated session |
| Status | Solved |

---

## Objective

The objective of this lab is to identify and exploit an authorization flaw where the application trusts a user-controlled `id` parameter.

The goal is to:

1. Identify how the application references user accounts.
2. Capture the authenticated request.
3. Identify the object reference used by the application.
4. Modify the `id` parameter.
5. Determine whether another user's information can be accessed.
6. Validate the authorization failure.
7. Document the evidence and security impact.

---

## Vulnerability Description

The application uses a request parameter to identify the account being requested.

For example:

```http
GET /my-account?id=wiener HTTP/2
Host: vulnerable-application.net
Cookie: session=...