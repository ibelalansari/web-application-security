# 🛡️ Web Application Security

### Security Assessment • Vulnerability Research • Penetration Testing

<p align="center">
  <img src="x100-assets/github-banner.png" alt="Web Application Security">
</p>

<p align="center">
  <strong>
    A practical Web Application Security portfolio focused on vulnerability
    discovery, manual validation, exploitation analysis, impact assessment,
    security reporting, remediation, and retesting.
  </strong>
</p>

<p align="center">
  🔎 Attack Surface Discovery
  &nbsp; • &nbsp;
  🗺️ Application Mapping
  &nbsp; • &nbsp;
  🔐 Authentication
  &nbsp; • &nbsp;
  🛡️ Authorization
  &nbsp; • &nbsp;
  💉 Injection
  &nbsp; • &nbsp;
  📦 File Upload
  &nbsp; • &nbsp;
  🧠 Business Logic
  &nbsp; • &nbsp;
  🧪 Manual Testing
  &nbsp; • &nbsp;
  📊 Risk Assessment
  &nbsp; • &nbsp;
  📝 Security Reporting
  &nbsp; • &nbsp;
  🔁 Retesting
</p>

---

# 🌐 About This Repository

Modern web applications expose complex attack surfaces across authentication,
authorization, APIs, business logic, input processing, file handling,
third-party dependencies, data protection, and application infrastructure.

Effective Web Application Security testing therefore requires more than
running automated scanners or collecting individual payloads.

A professional assessment requires understanding:

- Application functionality
- Attack surface and trust boundaries
- Authentication and session mechanisms
- Authorization models
- User-controlled input
- Application logic and workflows
- Security controls
- Vulnerability exploitability
- Real-world security impact
- Root cause and remediation

This repository documents that complete security-testing approach through
structured practical assessments and evidence-based technical documentation.

---

# 🏆 OWASP Top 10:2025

This repository is organized around the **OWASP Top 10:2025**, a widely
recognized awareness framework for the most critical web application security
risks.

The OWASP Top 10:2025 contains the following ten categories:

| ID | Category | Primary Security Focus |
|---|---|---|
| **A01:2025** | Broken Access Control | Authorization, IDOR, privilege escalation |
| **A02:2025** | Security Misconfiguration | Insecure configuration and deployment |
| **A03:2025** | Software Supply Chain Failures | Dependencies, build systems, packages and software ecosystem |
| **A04:2025** | Cryptographic Failures | Sensitive data protection and cryptographic controls |
| **A05:2025** | Injection | SQL Injection, XSS, command injection and related attacks |
| **A06:2025** | Insecure Design | Business logic and design-level security weaknesses |
| **A07:2025** | Authentication Failures | Authentication, sessions and credential security |
| **A08:2025** | Software or Data Integrity Failures | Integrity verification, deserialization and trusted artifacts |
| **A09:2025** | Security Logging & Alerting Failures | Security logging, monitoring and alerting |
| **A10:2025** | Mishandling of Exceptional Conditions | Error handling, failing open and abnormal-state handling |

> OWASP Top 10:2025 is the primary security framework used to structure this
> portfolio.

---

# 🔬 Security Assessment Methodology

The assessments documented in this repository follow a structured workflow:

```text
┌───────────────────────────────┐
│ 1. Reconnaissance             │
│    Attack Surface Discovery   │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│ 2. Application Mapping        │
│    Endpoints • Parameters     │
│    Roles • Trust Boundaries   │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│ 3. Security Testing           │
│    Manual • Controlled Tests  │
│    Burp Suite Analysis        │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│ 4. Vulnerability Validation   │
│    Reproduction • PoC         │
│    Evidence Collection        │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│ 5. Impact & Risk Assessment   │
│    Confidentiality            │
│    Integrity • Availability    │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│ 6. Security Reporting         │
│    Technical Findings         │
│    Evidence • Impact          │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│ 7. Remediation                │
│    Preventive Security        │
│    Controls                   │
└───────────────┬───────────────┘
                │
                ▼
┌───────────────────────────────┐
│ 8. Retesting                  │
│    Validate Security Fix      │
└───────────────────────────────┘
```

---

# 🧩 Security Testing Areas

The portfolio covers practical testing across multiple areas of web
application security.

### 🔐 Authentication & Session Security

- Authentication bypass
- Credential handling
- Session management
- Session fixation
- Password-related weaknesses
- Authentication workflow analysis

### 🛡️ Authorization & Access Control

- Broken access control
- IDOR / BOLA
- Horizontal privilege escalation
- Vertical privilege escalation
- Forced browsing
- Object-level authorization

### 💉 Injection

- SQL Injection
- UNION-based SQL Injection
- Blind SQL Injection
- Command Injection
- Cross-Site Scripting
- Server-Side Template Injection
- Other injection vectors

### 📦 File & Resource Handling

- Unrestricted file upload
- Malicious file upload
- File type validation
- Web shell upload
- Path traversal
- File inclusion

### 🌐 HTTP & Application Logic

- HTTP request manipulation
- Parameter tampering
- Security control bypass
- Business logic weaknesses
- Request/response analysis
- Trust boundary analysis

### 🔎 Information Disclosure

- Sensitive data exposure
- Error-based information disclosure
- Application metadata exposure
- Database information disclosure
- Credential disclosure

---

# 🧰 Tools & Technologies

| Category | Tools / Technologies |
|---|---|
| **Web Security Testing** | Burp Suite Professional |
| **Browser Testing** | Firefox |
| **Security Training** | PortSwigger Web Security Academy |
| **Operating System** | Kali Linux |
| **HTTP Analysis** | Burp Proxy, Repeater |
| **Version Control** | Git |
| **Repository** | GitHub |
| **Documentation** | Markdown |
| **Testing Method** | Manual Security Testing |

---

# 📂 Repository Structure

```text
web-application-security/
│
├── A01-Broken-Access-Control/
│
├── A02-Security-Misconfiguration/
│
├── A03-Software-Supply-Chain-Failures/
│
├── A04-Cryptographic-Failures/
│
├── A05-Injection/
│   │
│   └── Labs/
│       │
│       └── 01-PortSwigger-SQL-Injection/
│           ├── 01. Hidden-Data-Retrieval/
│           ├── 02. Authentication-Bypass/
│           ├── 03. UNION-Based-SQL-Injection/
│           ├── 05-File-Upload-RCE-via-Web-Shell/
│           └── ...
│
├── A06-Insecure-Design/
│
├── A07-Authentication-Failures/
│
├── A08-Software-or-Data-Integrity-Failures/
│
├── A09-Security-Logging-and-Alerting-Failures/
│
├── A10-Mishandling-of-Exceptional-Conditions/
│
└── x100-assets/
```

---

# 📁 Lab Documentation Structure

Practical security labs use a structured documentation model where applicable:

```text
Lab/
│
├── burp/
│
├── payloads/
│
├── screenshots/
│
├── README.md
├── notes.md
├── references.md
└── report.md
```

### `README.md`

Provides a concise technical overview of the vulnerability, methodology,
exploitation process, evidence, impact, remediation, and result.

### `notes.md`

Contains supporting technical notes and observations made during testing.

### `payloads/`

Contains relevant test payloads used during authorized security testing.

### `burp/`

Contains relevant Burp Suite project artifacts or request/response evidence.

### `screenshots/`

Contains visual evidence supporting vulnerability validation and lab
completion.

### `report.md`

Contains detailed security finding documentation and assessment information.

### `references.md`

Contains relevant technical references and security resources.

---

# 🧪 Evidence-Driven Testing

A key principle of this portfolio is **evidence-based vulnerability
validation**.

Each practical assessment aims to demonstrate:

```text
Request
   ↓
Security Control
   ↓
Manipulation
   ↓
Observed Behavior
   ↓
Vulnerability Validation
   ↓
Impact
   ↓
Remediation
```

Evidence may include:

- HTTP requests
- HTTP responses
- Burp Suite Proxy captures
- Burp Suite Repeater requests
- Payload testing
- Application responses
- Authentication results
- Lab completion evidence

Sensitive information is treated carefully and should be redacted before
publishing evidence outside controlled environments.

---

# 📊 Vulnerability Assessment Principles

The testing approach emphasizes:

### 1. Understand Before Exploiting

Understand the application's intended behavior before attempting to bypass
security controls.

### 2. Validate, Don't Assume

A suspected vulnerability should be reproduced and supported with technical
evidence.

### 3. Measure Real Impact

The presence of a vulnerability is only part of an assessment. Its practical
security impact must also be established.

### 4. Identify Root Cause

Find the underlying security weakness rather than documenting only the
observable symptom.

### 5. Recommend Practical Remediation

Security findings should provide actionable recommendations that developers
and engineering teams can implement.

### 6. Retest the Fix

A security control should be tested again after remediation to verify that the
vulnerability has actually been addressed.

---

# 📝 Security Finding Documentation

Security findings are structured around the following concepts:

```text
Finding
├── Vulnerability
├── Location
├── Description
├── Attack Vector
├── Proof of Concept
├── Evidence
├── Security Impact
├── Root Cause
├── Severity
├── Remediation
└── Retesting
```

This approach keeps technical findings understandable to both security
professionals and development teams.

---

# 🎓 Practical Security Skills

This portfolio demonstrates practical experience with:

- Web application attack-surface analysis
- HTTP request/response analysis
- Authentication testing
- Authorization testing
- Access-control testing
- SQL Injection testing
- UNION-based SQL Injection
- Database enumeration
- Credential extraction
- File upload security testing
- Remote Code Execution validation
- Parameter manipulation
- Burp Suite Proxy
- Burp Suite Repeater
- Manual vulnerability validation
- Security evidence collection
- Impact assessment
- Security remediation
- Technical security documentation

---

# ⚖️ Responsible Security Testing

All testing documented in this repository is intended for:

- Authorized security labs
- Intentionally vulnerable applications
- Controlled testing environments
- Systems for which explicit authorization has been obtained

Security testing techniques must never be used against systems without
appropriate authorization.

---

# 📚 Primary Reference

This portfolio uses the **OWASP Top 10:2025** as its primary application
security framework.

The 2025 edition introduced changes including the expansion of software
supply-chain risks under A03 and the introduction of Mishandling of Exceptional
Conditions as A10. :contentReference[oaicite:1]{index=1}

Official OWASP reference:

https://owasp.org/Top10/2025/