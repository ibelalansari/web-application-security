# Technical Notes — IDOR

## 1. Core Concept

Insecure Direct Object Reference (IDOR) is an access-control vulnerability that occurs when an application exposes a reference to an internal object and fails to properly verify whether the authenticated user is authorized to access that object.

The reference may appear in:

- URL parameters
- Path parameters
- Query parameters
- Form fields
- JSON request bodies
- API parameters

Example:

```http
GET /my-account?id=wiener HTTP/2