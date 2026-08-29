# 🔐 PortSwigger Lab — User Role Controlled by Request Parameter

## 📌 Lab Overview

This lab demonstrates a **Broken Access Control** vulnerability where a user's privileges are controlled by a client-side request parameter.

The vulnerability occurs when the application relies on user-controlled input to determine authorization privileges instead of enforcing access control on the server side.

---

## 🎯 Objective

The objective of this lab is to:

- Identify the application's authorization mechanism.
- Analyze how user roles are represented in HTTP requests.
- Determine whether privilege information can be controlled by the client.
- Validate unauthorized access to privileged functionality.
- Assess the security impact of the authorization weakness.
- Document appropriate remediation measures.

---

## 🏷️ Vulnerability Classification

| Category | Details |
|---|---|
| OWASP Top 10 | A01: Broken Access Control |
| Vulnerability Type | Privilege Escalation / Broken Authorization |
| Testing Type | Manual Web Application Security Testing |
| Primary Tool | Burp Suite |
| Environment | PortSwigger Web Security Academy |

---

## 🧩 Lab Scenario

The application implements different user roles with different levels of access.

During testing, the authorization mechanism is analyzed to determine whether the application properly validates the user's privileges on the server side.

The assessment focuses on identifying whether a normal user can influence role-related request parameters and obtain functionality intended only for a higher-privileged account.

---

## 🔎 Attack Surface

The following areas are relevant to this assessment:

- Authentication and session management
- Authorization controls
- Privileged functionality
- HTTP request parameters
- Client-controlled role information
- Administrative functionality

---

## 🧪 Testing Methodology

The assessment follows a structured authorization testing workflow:

1. Authenticate to the application.
2. Identify the privileges associated with the current user.
3. Browse the application and map available functionality.
4. Capture relevant HTTP requests using Burp Suite.
5. Inspect request parameters and session-related information.
6. Identify parameters associated with user privileges or roles.
7. Test whether authorization decisions can be influenced by client-controlled input.
8. Compare application behavior before and after controlled request modification.
9. Validate whether privileged functionality becomes accessible.
10. Document the evidence and security impact.

---

## 🛠️ Burp Suite Analysis

### Request Interception

Relevant application requests were captured using **Burp Suite Proxy**.

The captured request was analyzed for:

- HTTP method
- Request path
- Query parameters
- Request body
- Cookies
- Session identifiers
- Authorization-related parameters

### Request Analysis

The assessment focused on determining whether role or privilege information was being trusted directly from the client request.

> ⚠️ Sensitive session tokens, credentials, and production secrets should never be included in public documentation.

---

## 🔬 Vulnerability Validation

The authorization behavior was tested by modifying the relevant client-controlled input and replaying the request.

The application's response was then compared with the original behavior.

### Expected Secure Behavior

A properly implemented application should:

- Determine the user's privileges server-side.
- Ignore client-controlled privilege information.
- Verify authorization for every privileged operation.
- Return an appropriate authorization failure when access is not permitted.

### Observed Behavior

Document the behavior observed during the lab:
