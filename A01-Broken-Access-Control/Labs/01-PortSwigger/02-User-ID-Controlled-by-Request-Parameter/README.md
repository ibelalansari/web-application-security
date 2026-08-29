# 🔐 IDOR — User ID Controlled by Request Parameter

## Overview

This lab demonstrates an **Insecure Direct Object Reference (IDOR)**
vulnerability caused by insufficient server-side authorization controls.

The application uses a user-controlled request parameter to identify which
user account information should be returned. Because the server does not
properly verify whether the authenticated user is authorized to access the
requested account, modifying the parameter allows access to another user's
account information.

This is a classic **Broken Access Control** scenario where authentication is
present, but authorization enforcement is insufficient.

---

## 🎯 Lab Objective

Access another user's account information by manipulating the user-controlled
`id` request parameter while maintaining the existing authenticated session.

### Target Request

```http
GET /my-account?id=wiener HTTP/2