# 🛡️ OWASP Top 10 — Web Application Security

## Web Application Security Assessment, Testing & Vulnerability Validation Framework

> A structured security research and assessment repository built around the **OWASP Top 10:2025**, covering vulnerability discovery, manual security testing, validation, impact analysis, evidence collection, reporting, and remediation-oriented assessment.

---

## 🎯 Purpose

The OWASP Top 10 provides a practical foundation for understanding and assessing critical risks affecting modern web applications.

This repository transforms those risk categories into a **structured security testing workflow** rather than treating the OWASP Top 10 as a simple checklist.

The assessment approach is centered around:

**Understand → Discover → Map → Test → Validate → Assess Impact → Document → Remediate → Retest**

The goal is to connect individual vulnerabilities with the broader security context of:

- Application architecture
- Attack surface
- Trust boundaries
- Authentication
- Authorization
- Input handling
- Business logic
- Security controls
- Data protection
- Error handling
- Logging and alerting
- Software and dependency integrity

---

# 🔐 Security Assessment Lifecycle

<p align="center">

<img src="../02-assets/security-assessment-lifecycle.png"
     alt="Web Application Security Assessment Lifecycle">

</p>

### Assessment Flow

```text
WEB APPLICATION
       │
       ▼
ATTACK SURFACE DISCOVERY
       │
       ▼
APPLICATION MAPPING
       │
       ├── Endpoints
       ├── Parameters
       ├── Inputs
       ├── APIs
       ├── Roles
       └── Data Flows
       │
       ▼
SECURITY CONTROL ANALYSIS
       │
       ├── Authentication
       ├── Authorization
       ├── Session Management
       ├── Input Validation
       ├── Access Control
       └── Security Boundaries
       │
       ▼
MANUAL SECURITY TESTING
       │
       ▼
VULNERABILITY VALIDATION
       │
       ▼
IMPACT ANALYSIS
       │
       ▼
RISK ASSESSMENT
       │
       ▼
EVIDENCE & REPORTING
       │
       ▼
REMEDIATION
       │
       ▼
RETEST
       │
       └───────────────🔁
```

---

# 📚 OWASP Top 10:2025

The repository is organized around the ten OWASP Top 10:2025 risk categories. :contentReference[oaicite:1]{index=1}

| ID | Category | Primary Security Focus |
|---|---|---|
| **A01** | Broken Access Control | Authorization, privilege boundaries, object/function access |
| **A02** | Security Misconfiguration | Application, server, framework and security configuration |
| **A03** | Software Supply Chain Failures | Dependencies, build systems, packages and software ecosystem |
| **A04** | Cryptographic Failures | Encryption, key management, secrets and protected data |
| **A05** | Injection | SQLi, XSS, command injection and other interpreter injection |
| **A06** | Insecure Design | Threat modeling, business logic and security architecture |
| **A07** | Authentication Failures | Authentication, sessions, credentials and identity controls |
| **A08** | Software or Data Integrity Failures | Integrity verification, trusted data/code and update mechanisms |
| **A09** | Security Logging & Alerting Failures | Security events, logging, detection and alerting |
| **A10** | Mishandling of Exceptional Conditions | Error handling, abnormal states, fail-open behavior and logical failures |

OWASP introduced **Software Supply Chain Failures** and **Mishandling of Exceptional Conditions** as new categories in the 2025 edition, while SSRF was incorporated into Broken Access Control. :contentReference[oaicite:2]{index=2}

---

# 🧭 Assessment Methodology

Each category is approached from an application-security assessment perspective.

## 01 — Reconnaissance & Attack Surface

Identify and understand:

- Application entry points
- HTTP methods
- Parameters
- Query strings
- Request bodies
- Headers
- Cookies
- Authentication endpoints
- API endpoints
- Administrative interfaces
- File upload functionality
- External integrations
- Hidden or undocumented functionality

---

## 02 — Application Mapping

Build a practical model of the application:

```text
Users
  │
  ├── Anonymous
  ├── Standard User
  ├── Privileged User
  └── Administrator
        │
        ▼
Application
        │
        ├── Web Interface
        ├── REST/API
        ├── Authentication
        ├── Business Logic
        ├── File Handling
        └── Data Layer
```

The objective is to understand **how trust and privilege flow through the application**.

---

## 03 — Security Control Analysis

Security controls are evaluated across:

- Authentication
- Authorization
- Session management
- Input validation
- Output encoding
- Access control
- Cryptographic protection
- Security headers
- Error handling
- Logging
- Rate limiting
- File handling
- API security
- Trust boundaries

---

## 04 — Manual Security Testing

The repository emphasizes **manual security validation** rather than relying exclusively on automated scanners.

Testing may include:

- Request manipulation
- Parameter tampering
- Role manipulation
- Object identifier manipulation
- Authentication testing
- Session testing
- Input mutation
- Encoding manipulation
- Business-logic testing
- API request modification
- Security-control bypass testing
- Boundary-condition testing

---

## 05 — Vulnerability Validation

Potential weaknesses are validated through controlled testing.

A finding is not treated as a confirmed vulnerability simply because a scanner or unusual response suggests it.

Validation focuses on:

```text
Observation
     ↓
Hypothesis
     ↓
Controlled Test
     ↓
Reproducibility
     ↓
Security Impact
     ↓
Confirmed Finding
```

---

# 🧪 Testing Coverage

## A01 — Broken Access Control

Focus areas include:

- Horizontal privilege escalation
- Vertical privilege escalation
- IDOR / object-level authorization
- Function-level authorization
- Role manipulation
- Parameter-based access control
- Missing authorization checks
- Forced browsing
- Administrative endpoint exposure
- Access-control bypass
- Server-Side Request Forgery (SSRF) within the 2025 category context

---

## A02 — Security Misconfiguration

Assessment areas include:

- Default configurations
- Debug functionality
- Exposed administrative interfaces
- Security headers
- CORS configuration
- Directory listing
- Verbose errors
- Unnecessary services
- Framework configuration
- Server configuration
- XML parser configuration
- Cloud/application configuration

---

## A03 — Software Supply Chain Failures

Assessment areas include:

- Third-party dependencies
- Dependency integrity
- Package management
- Build pipelines
- CI/CD security
- Dependency sources
- Artifact integrity
- Update mechanisms
- Compromised dependencies
- Software distribution trust

This category expands the previous vulnerable/outdated-component concept into the broader software supply-chain ecosystem. :contentReference[oaicite:3]{index=3}

---

## A04 — Cryptographic Failures

Assessment areas include:

- Weak cryptographic algorithms
- Insecure encryption
- Weak hashing
- Password storage
- Key management
- Hardcoded secrets
- Sensitive information exposure
- Improper TLS usage
- Insecure random values
- Cryptographic configuration

---

## A05 — Injection

Testing coverage includes:

### SQL Injection

- UNION-based SQL injection
- Error-based SQL injection
- Blind SQL injection
- Boolean-based techniques
- Conditional responses
- Time-based techniques
- Second-order injection
- Filter/WAF bypass concepts
- Database enumeration
- Column enumeration

### Other Injection Classes

- Cross-Site Scripting
- Command Injection
- LDAP Injection
- XPath Injection
- Template Injection
- Header Injection
- Other interpreter-driven injection scenarios

---

## A06 — Insecure Design

Assessment focuses on security weaknesses originating from design decisions:

- Threat modeling
- Trust boundaries
- Business-logic flaws
- Abuse cases
- Missing security controls
- Insecure workflows
- Improper privilege models
- Security assumptions
- Insecure architecture
- Failures in security-by-design

---

## A07 — Authentication Failures

Assessment areas include:

- Authentication mechanisms
- Login workflows
- Credential handling
- Session management
- Password policies
- Brute-force resistance
- Account enumeration
- Authentication bypass
- Password reset mechanisms
- Session invalidation
- Multi-factor authentication controls
- Remember-me functionality

---

## A08 — Software or Data Integrity Failures

Assessment areas include:

- Integrity verification
- Trusted data handling
- Serialization/deserialization
- Software update mechanisms
- Untrusted data sources
- CI/CD integrity
- Dependency integrity
- Code/data trust boundaries
- Unsigned or improperly validated artifacts

---

## A09 — Security Logging & Alerting Failures

Assessment areas include:

- Authentication logging
- Authorization events
- Security-event logging
- Sensitive-data handling in logs
- Log integrity
- Log injection
- Monitoring coverage
- Alert generation
- Detection visibility
- Incident investigation support

Logging without effective alerting can significantly reduce the operational value of security telemetry. :contentReference[oaicite:4]{index=4}

---

## A10 — Mishandling of Exceptional Conditions

Assessment areas include:

- Improper error handling
- Fail-open behavior
- Unexpected application states
- Missing parameters
- Invalid state transitions
- Exception handling
- Sensitive error messages
- Improper privilege handling during errors
- Boundary conditions
- Logical failures

This is a new OWASP Top 10:2025 category focused on security weaknesses arising from abnormal or unexpected conditions. :contentReference[oaicite:5]{index=5}

---

# 🛠️ Security Testing Workflow

A practical assessment can be represented as:

```text
Reconnaissance
      ↓
Attack Surface Discovery
      ↓
Application Mapping
      ↓
Authentication Analysis
      ↓
Authorization Analysis
      ↓
Input & Output Analysis
      ↓
Security Control Testing
      ↓
Manual Exploitation
      ↓
Vulnerability Validation
      ↓
Impact Analysis
      ↓
Risk Assessment
      ↓
Evidence Collection
      ↓
Security Reporting
      ↓
Remediation Guidance
      ↓
Retesting
```

---

# 🔬 Evidence-Driven Validation

Each documented security finding is intended to provide a reproducible technical trail.

Typical evidence may include:

```text
Request
   ↓
Modified Request
   ↓
Server Response
   ↓
Observed Behavior
   ↓
Security Impact
   ↓
Proof of Concept
   ↓
Remediation
```

Where applicable, documentation may include:

- HTTP requests
- HTTP responses
- Burp Suite evidence
- Screenshots
- Payloads
- Reproduction steps
- Technical analysis
- Impact analysis
- References
- Remediation recommendations

---

# 📊 Risk-Oriented Analysis

A vulnerability should be evaluated beyond the technical weakness itself.

Assessment considers:

```text
Attack Vector
      +
Exploitability
      +
Required Privileges
      +
User Interaction
      +
Technical Impact
      +
Business Impact
      ↓
Overall Risk
```

Risk is context-dependent. The same technical vulnerability can have significantly different consequences depending on application exposure, affected data, user roles, business function, and threat model. OWASP's 2025 methodology likewise considers exploitability, likelihood, technical impact, and business context. :contentReference[oaicite:6]{index=6}

---

# 📝 Vulnerability Documentation Model

A professional finding should answer:

### What is vulnerable?

Clearly identify the affected component, endpoint, parameter, workflow, or control.

### Why is it vulnerable?

Explain the underlying security weakness.

### How can it be reproduced?

Provide clear and repeatable validation steps.

### What can an attacker achieve?

Describe realistic technical impact.

### What is the business impact?

Connect the technical issue to confidentiality, integrity, availability, authorization, data exposure, or business functionality.

### How should it be remediated?

Provide practical remediation guidance.

### How can remediation be verified?

Define a retest approach.

---

# 📁 Repository Structure

```text
01-OWASP-Top-10/
│
├── A01-Broken-Access-Control/
│   ├── README.md
│   ├── Labs/
│   │   ├── 01-PortSwigger/
│   │   └── 02-Custom-Labs/
│   └── Notes.txt
│
├── A02-Security-Misconfiguration/
│   ├── README.md
│   ├── Labs/
│   │   ├── 01-PortSwigger/
│   │   └── 02-Custom-Labs/
│   └── Notes.txt
│
├── A03-Software-Supply-Chain-Failures/
│   ├── README.md
│   ├── Labs/
│   │   ├── 01-PortSwigger/
│   │   └── 02-Custom-Labs/
│   └── Notes.txt
│
├── A04-Cryptographic-Failures/
│   ├── README.md
│   ├── Labs/
│   │   ├── 01-PortSwigger/
│   │   └── 02-Custom-Labs/
│   └── Notes.txt
│
├── A05-Injection/
│   ├── README.md
│   ├── Labs/
│   │   ├── 01-PortSwigger-SQL-Injection/
│   │   └── 02-Custom-Labs/
│   └── Notes.txt
│
├── A06-Insecure-Design/
│   ├── README.md
│   ├── Labs/
│   │   ├── 01-PortSwigger/
│   │   └── 02-Custom-Labs/
│   └── Notes.txt
│
├── A07-Authentication-Failures/
│   ├── README.md
│   ├── Labs/
│   │   ├── 01-PortSwigger/
│   │   └── 02-Custom-Labs/
│   └── Notes.txt
│
├── A08-Software-or-Data-Integrity-Failures/
│   ├── README.md
│   ├── Labs/
│   │   ├── 01-PortSwigger/
│   │   └── 02-Custom-Labs/
│   └── Notes.txt
│
├── A09-Security-Logging-and-Alerting-Failures/
│   ├── README.md
│   ├── Labs/
│   │   ├── 01-PortSwigger/
│   │   └── 02-Custom-Labs/
│   └── Notes.txt
│
└── A10-Mishandling-of-Exceptional-Conditions/
    ├── README.md
    ├── Labs/
    │   ├── 01-PortSwigger/
    │   └── 02-Custom-Labs/
    └── Notes.txt
```

---

# 🧰 Security Testing Toolkit

The repository is designed around practical application-security testing workflows using tools and techniques such as:

- **Burp Suite**
- **Browser Developer Tools**
- **HTTP/HTTPS analysis**
- **Manual request manipulation**
- **API testing**
- **PortSwigger Web Security Academy**
- **OWASP testing methodologies**
- **Custom test cases**
- **Command-line security tooling**
- **Evidence-driven documentation**

The objective is not tool dependence.

> **Tools accelerate testing. Understanding the application validates the finding.**

---

# 🎯 Security Assessment Principles

### 01 — Understand Before Exploiting

Application behavior and trust boundaries should be understood before attempting exploitation.

### 02 — Validate Before Reporting

A suspected weakness should be reproduced and technically validated before being treated as a confirmed finding.

### 03 — Prove Impact

Technical behavior should be connected to realistic security consequences.

### 04 — Minimize Assumptions

Testing should be based on observable application behavior rather than unsupported assumptions.

### 05 — Document Reproducibly

Another security professional should be able to understand and reproduce the finding from the evidence provided.

### 06 — Remediation Matters

A security assessment is more valuable when it helps the development team understand how to fix and retest the weakness.

---

# 📌 OWASP Top 10 Is a Foundation — Not the Entire AppSec Universe

The OWASP Top 10 is an important awareness and assessment foundation, but it is not intended to represent complete application-security coverage.

For comprehensive application security verification, OWASP recommends considering standards such as the **OWASP Application Security Verification Standard (ASVS)** alongside the Top 10. :contentReference[oaicite:7]{index=7}

This repository therefore treats the Top 10 as a structured entry point into broader:

- Web application security
- API security
- Authentication security
- Authorization testing
- Secure design
- Vulnerability assessment
- Penetration testing
- Security validation
- Risk analysis
- Security reporting

---

# 🔗 References

- [OWASP Top 10:2025](https://owasp.org/Top10/2025/)
- [OWASP Top 10:2025 Introduction](https://owasp.org/Top10/2025/0x00_2025-Introduction/)
- [OWASP Application Security Verification Standard](https://owasp.org/www-project-application-security-verification-standard/)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/)
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [PortSwigger Web Security Academy](https://portswigger.net/web-security)

---

# ⚠️ Responsible Security Testing

All testing documented in this repository is intended for:

- Authorized security assessments
- Deliberately vulnerable applications
- Security laboratories
- Educational environments
- Responsible vulnerability research

Testing against systems without authorization is not permitted.

---

## 🛡️ Security Mindset

```text
DISCOVER
   ↓
UNDERSTAND
   ↓
TEST
   ↓
VALIDATE
   ↓
PROVE IMPACT
   ↓
DOCUMENT
   ↓
REMEDIATE
   ↓
RETEST
```

> **Security is not just finding vulnerabilities.  
> It is understanding how systems fail, proving why they fail, and helping make them resilient.**