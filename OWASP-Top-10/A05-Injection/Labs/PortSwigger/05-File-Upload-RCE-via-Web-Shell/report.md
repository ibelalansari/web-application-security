# Vulnerability Assessment Report

## 1. Executive Summary

A Remote Code Execution (RCE) vulnerability was identified in the application's avatar upload functionality.

The application allowed an authenticated user to upload a server-side executable PHP file without adequate validation. The uploaded file was stored in a web-accessible location and subsequently interpreted by the web server.

This allowed the uploaded PHP payload to execute server-side code and retrieve data from the application environment.

**Risk Rating:** Critical

**Vulnerability:** Unrestricted File Upload leading to Remote Code Execution

**Affected Functionality:** Avatar Upload

**Testing Environment:** PortSwigger Web Security Academy

---

## 2. Vulnerability Details

### Vulnerability Classification

**Primary vulnerability:**

Unrestricted File Upload

**Impact:**

Remote Code Execution

**CWE:**

CWE-434 — Unrestricted Upload of File with Dangerous Type

### Description

The avatar upload functionality did not sufficiently restrict the type of files that could be uploaded.

An attacker with valid application access could upload a crafted PHP file instead of a legitimate image.

Because the uploaded file remained accessible through the web application and was interpreted as PHP, the attacker-controlled code was executed by the server.

---

## 3. Affected Functionality

The vulnerable functionality was the application's avatar upload feature.

The relevant request used:

```text
POST /my-account/avatar