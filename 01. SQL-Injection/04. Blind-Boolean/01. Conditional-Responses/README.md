# Blind SQL Injection with Conditional Responses

## Lab Overview

- **Platform:** PortSwigger Web Security Academy
- **Vulnerability:** Blind SQL Injection
- **Technique:** Conditional Responses / Boolean Inference
- **Injection Point:** `TrackingId` Cookie
- **Target:** `administrator`

## Objective

The objective of this lab was to identify and exploit a Blind SQL Injection vulnerability where database information is not directly returned in the application's response.

Instead, the application's response behavior was used as a Boolean oracle to determine whether injected SQL conditions evaluated to TRUE or FALSE.

## Methodology

1. Captured a normal request and established a baseline response.
2. Tested Boolean TRUE and FALSE conditions.
3. Confirmed the existence of the `administrator` user.
4. Determined the password length through conditional responses.
5. Tested password characters position by position.
6. Used Burp Suite Intruder to automate repetitive character testing.
7. Verified the recovered information and completed the lab.

## Evidence

The testing process is documented through the following screenshots:

- `01-lab-overview.png` — Lab overview
- `02-normal-request.png` — Baseline request
- `03-administrator-account.png` — Administrator account validation
- `04-conditional-response-welcome.png` — Conditional response indicator
- `05-password-character-discovery.png` — Password character discovery
- `06-password-retrieved.png` — Password retrieval
- `07-lab-solved.png` — Final lab verification

## Key Learning

Blind SQL Injection does not require the application to directly display database results.

A predictable difference in:

- Response content
- Response length
- HTTP status
- Response timing

can be used as a **Boolean oracle**.

The application effectively answers questions such as:

```text
Is this condition TRUE?
        ↓
Application response
        ↓
YES / NO