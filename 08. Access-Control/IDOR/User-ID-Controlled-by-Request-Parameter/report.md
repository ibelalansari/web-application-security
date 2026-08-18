# Security Assessment Report

## Finding Information

| Field | Details |
|---|---|
| Finding | Insecure Direct Object Reference (IDOR) |
| Category | Broken Access Control |
| Affected Function | User Account |
| Affected Parameter | `id` |
| Severity | High* |
| Authentication Required | Yes |
| Testing Tool | Burp Suite Professional |
| Status | Confirmed |

\* Severity in a real application depends on the sensitivity of the exposed data and the overall business impact.

---

## Executive Summary

An Insecure Direct Object Reference (IDOR) vulnerability was identified in the application's account functionality.

The application uses a client-controlled `id` parameter to determine which user account is returned. The server did not adequately verify whether the authenticated user was authorized to access the requested account.

As a result, an authenticated user was able to request another user's account information by modifying the `id` parameter while maintaining the same authenticated session.

---

## Vulnerability Description

The application accepts a user identifier through the following request parameter:

```http
GET /my-account?id=wiener HTTP/2