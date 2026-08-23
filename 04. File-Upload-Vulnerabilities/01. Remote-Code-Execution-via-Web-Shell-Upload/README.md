# Remote Code Execution via Web Shell Upload

## Overview

This lab demonstrates a Remote Code Execution (RCE) vulnerability caused by an insecure file-upload mechanism.

The application allows an attacker-controlled PHP file to be uploaded through the avatar functionality. Because the uploaded file remains accessible from a web-accessible location and PHP execution is permitted, the uploaded file can be executed by requesting its URL.

## Lab

**Platform:** PortSwigger Web Security Academy

**Lab:** Remote code execution via web shell upload

**Vulnerability Class:** File Upload Vulnerability

**Impact:** Remote Code Execution

## Objective

The objective was to identify an insecure file-upload functionality, upload a server-side PHP payload, and demonstrate that the uploaded file is executed by the web server.

## Methodology

### 1. Authentication

First, I authenticated to the lab application using the provided test credentials.

Evidence:

![Authentication](screenshots/01-authentication.png)

---

### 2. Payload Preparation

A PHP payload was created to demonstrate server-side code execution.

The payload is stored in:

`payloads/exploit.php`

Payload:

```php
<?php
echo file_get_contents('/home/carlos/secret');
?>