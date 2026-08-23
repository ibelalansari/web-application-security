# Security Assessment Report

## 1. Finding

**Title:** Remote Code Execution via Insecure File Upload

**Severity:** Critical

**Vulnerability Type:** File Upload Vulnerability

**Impact:** Remote Code Execution (RCE)

**Target:** PortSwigger Web Security Academy training lab

**Status:** Confirmed

---

## 2. Executive Summary

The application contains an insecure file-upload vulnerability in the avatar upload functionality.

An authenticated user can upload a PHP file through the avatar upload mechanism. The uploaded file is stored in a web-accessible location where the server processes PHP files as executable code.

By requesting the uploaded PHP resource, server-side code execution can be demonstrated.

This vulnerability can potentially allow an attacker to execute arbitrary code with the privileges of the web application process.

---

## 3. Affected Functionality

The vulnerable functionality is the application's avatar/profile image upload mechanism.

The relevant endpoint observed during testing was:

```text
POST /my-account/avatar