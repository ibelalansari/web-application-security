
---

# 2️⃣ `notes.md`

```markdown
# Notes — Blind SQL Injection with Conditional Responses

## 1. What is Blind SQL Injection?

Blind SQL Injection occurs when an application is vulnerable to SQL Injection, but the database query result is not directly displayed in the application's response.

Instead, the attacker observes indirect changes in application behavior.

For example:

```text
SQL Condition
     ↓
Database evaluates condition
     ↓
TRUE / FALSE
     ↓
Different application response