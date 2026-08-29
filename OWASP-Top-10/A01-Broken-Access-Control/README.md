# 🔐 A01: Broken Access Control

A professional documentation and practical security testing collection focused on **Broken Access Control**, aligned with the **OWASP Top 10:2025**.

---

## 🎯 Overview

Broken Access Control occurs when an application fails to properly enforce what authenticated or unauthenticated users are allowed to access or perform.

Effective access control ensures that users can access only the resources and functionality permitted by their intended role, identity, and security policy.

This section documents practical analysis and testing of access control weaknesses across web applications.

---

## 🔎 Security Testing Focus

Testing focuses on identifying weaknesses in:

- Authentication-dependent authorization
- Horizontal access control
- Vertical access control
- Object-level authorization
- Function-level authorization
- Resource ownership enforcement
- Privilege escalation
- Forced browsing
- Administrative functionality
- Access control enforcement across HTTP methods
- Client-side versus server-side authorization
- Multi-step workflow authorization

---

## 🧪 Vulnerability Classes

### IDOR — Insecure Direct Object Reference

Testing whether users can access another user's resources by modifying object identifiers.

Examples:

- User IDs
- Account IDs
- Order IDs
- Document IDs
- Profile IDs
- API resource identifiers

---

### BOLA — Broken Object Level Authorization

Testing authorization controls around object-level access, particularly in APIs.

Focus areas include:

- Resource ownership
- Object identifiers
- User-to-object relationships
- Cross-user data access
- Unauthorized modification or deletion

---

### Horizontal Privilege Escalation

Testing whether one user can access or modify resources belonging to another user with the same privilege level.

---

### Vertical Privilege Escalation

Testing whether a lower-privileged user can access functionality intended for higher-privileged roles.

Examples:

- User → Moderator
- User → Manager
- User → Administrator

---

### Forced Browsing

Testing whether restricted functionality can be accessed directly by requesting hidden or administrative endpoints.

---

### Method-Based Access Control

Testing whether changing the HTTP method or request structure can bypass authorization controls.

Examples:

- GET → POST
- POST → PUT
- PUT → DELETE

---

## 🛠️ Testing Methodology

The assessment process follows a structured workflow:

1. Identify application roles and privilege levels
2. Map protected resources and functionality
3. Identify object identifiers and resource references
4. Capture legitimate requests
5. Compare requests between different user contexts
6. Modify identifiers and authorization-related parameters
7. Test horizontal access boundaries
8. Test vertical access boundaries
9. Test direct access to restricted endpoints
10. Validate authorization enforcement server-side
11. Assess security impact
12. Document evidence and remediation guidance

---

## 🧰 Tools

- Burp Suite
- Browser Developer Tools
- HTTP clients
- Web application testing environments
- Custom testing scripts where appropriate

---

## 📊 Evidence & Validation

Each validated finding may include:

- Request/response evidence
- Affected endpoint
- Affected parameter or object
- User privilege context
- Reproduction steps
- Security impact
- Risk assessment
- Remediation guidance

Sensitive information and production credentials should never be included in public documentation.

---

## 🧪 Practical Labs

Practical exercises are maintained under:

```text
Labs/
├── PortSwigger/
├── Custom-Labs/
└── ...