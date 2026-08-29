# 💉 A05: Injection

A professional documentation and research collection focused on **Injection vulnerabilities**, aligned with the **OWASP Top 10:2025**.

---

## 🎯 Overview

Injection vulnerabilities occur when untrusted input is interpreted as part of a command or query by an application, interpreter, or backend component.

This section documents the identification, analysis, validation, impact assessment, and remediation of injection vulnerabilities across web applications and related services.

The focus is on understanding how application input flows into interpreters, identifying insufficient input handling, and validating security impact through controlled testing.

---

## 🔍 Injection Vulnerability Types

### SQL Injection

- Union-based SQL Injection
- Error-based SQL Injection
- Boolean-based Blind SQL Injection
- Time-based Blind SQL Injection
- Out-of-band SQL Injection
- Second-order SQL Injection
- Filter and WAF bypass techniques

### Command Injection

- OS command injection
- Blind command injection
- Command execution through unsafe input handling

### Other Injection Classes

- LDAP Injection
- XPath Injection
- NoSQL Injection
- Expression Language Injection
- Server-Side Template Injection (SSTI)
- Other interpreter-based injection vulnerabilities

---

## 🧪 Security Testing Approach

### 1. Input Discovery

Identify application-controlled input points including:

- URL parameters
- Query parameters
- POST parameters
- JSON bodies
- HTTP headers
- Cookies
- File names and metadata
- API parameters
- Search and filtering functionality

### 2. Input Flow Analysis

Analyze how user-controlled input is processed by:

- Database queries
- Operating system commands
- Application interpreters
- Template engines
- Directory and file operations
- API back-end services

### 3. Injection Testing

Test whether application input is safely handled by introducing controlled test cases and observing application behavior.

Testing may include:

- Syntax-based testing
- Error-based analysis
- Boolean condition testing
- Time-based behavior analysis
- Response comparison
- Out-of-band interaction testing
- Filter and validation analysis

### 4. Vulnerability Validation

For each suspected vulnerability:

- Reproduce the behavior
- Confirm the injection point
- Determine the affected component
- Establish exploitability
- Assess potential security impact
- Collect supporting evidence

### 5. Impact Assessment

Validated findings are evaluated based on:

- Confidentiality impact
- Integrity impact
- Availability impact
- Authentication impact
- Data exposure
- Privilege implications
- Potential business impact

### 6. Remediation

Recommended remediation may include:

- Parameterized queries
- Prepared statements
- Safe APIs
- Strict input validation
- Context-aware output handling
- Secure command execution practices
- Least-privilege database accounts
- Proper encoding and escaping where appropriate
- Secure framework and library usage
- Defense-in-depth controls

---

## 🗄️ SQL Injection Research

SQL Injection is a major focus within this section.

Practical research covers multiple SQL Injection techniques, including:

```text
SQL Injection
├── Union-Based
├── Error-Based
├── Blind - Boolean
├── Blind - Time-Based
├── Out-of-Band
├── Second-Order
├── Filter Bypass
└── WAF Bypass