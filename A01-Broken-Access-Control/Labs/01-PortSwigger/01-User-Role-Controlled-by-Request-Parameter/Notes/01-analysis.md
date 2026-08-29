# Lab Analysis — User Role Controlled by Request Parameter

## Objective

Analyze an access control vulnerability where the user's role or privilege level is controlled by a client-side request parameter.

The objective is to determine whether a low-privileged user can manipulate a request parameter to access functionality intended for a higher-privileged user.

---

## Vulnerability Concept

The application relies on client-controlled input to determine the user's authorization level.

This creates a server-side authorization weakness because security-sensitive privilege information should never be trusted solely from the client.

### Security Principle

Authorization decisions must be enforced server-side.

The server should determine the authenticated user's privileges from trusted server-side state rather than accepting privilege information supplied by the client.

---

## Attack Surface

Potential attack surfaces include:

- HTTP request parameters
- Query parameters
- POST parameters
- Cookies
- Hidden form fields
- Headers
- Session-related values

Particular attention should be given to parameters that appear to represent:

- User roles
- Administrative privileges
- Account types
- Permission levels
- Access-control states

---

## Testing Methodology

1. Authenticate as a low-privileged user.
2. Identify functionality restricted to privileged users.
3. Capture the relevant HTTP request using Burp Suite.
4. Inspect request parameters for client-controlled authorization-related values.
5. Modify the suspected parameter.
6. Replay the modified request.
7. Compare the response with the original request.
8. Determine whether privileged functionality becomes accessible.
9. Validate the security impact.
10. Document the evidence and remediation.

---

## Burp Suite Testing

### Request Inspection

Review the captured request for parameters that may influence authorization decisions.

Focus on parameters whose values appear related to:

- Role
- User type
- Privilege
- Access level
- Administrative status

### Parameter Manipulation

Modify the suspected client-controlled value and resend the request.

The objective is to determine whether the server independently validates the user's authorization or blindly trusts the supplied value.

---

## Expected Secure Behavior

A secure application should:

- Determine authorization server-side.
- Validate permissions for every protected operation.
- Ignore client-controlled privilege indicators.
- Prevent privilege escalation through parameter manipulation.
- Return an appropriate authorization error when access is denied.

---

## Vulnerability Indicators

Potential indicators include:

- Access to administrator functionality from a low-privileged account.
- Successful execution of privileged actions after parameter modification.
- Different authorization behavior based solely on a client-controlled value.
- Missing or inadequate server-side authorization checks.

---

## Security Impact

If successfully exploited, this type of vulnerability may allow:

- Horizontal privilege escalation
- Vertical privilege escalation
- Unauthorized administrative access
- Unauthorized modification of application data
- Access to restricted functionality

The final impact depends on the privileges associated with the affected functionality.

---

## Evidence

Document the following during testing:

- Original request
- Modified request
- Relevant parameter
- Original response
- Modified response
- Resulting access level
- Burp Suite screenshots

---

## Remediation

Authorization decisions should be enforced entirely on the server.

The application should:

1. Identify the authenticated user from trusted server-side session state.
2. Retrieve the user's permissions from trusted server-side data.
3. Validate authorization before every privileged operation.
4. Never trust client-controlled role or privilege parameters.
5. Apply centralized and consistent access-control checks.
6. Log security-relevant authorization failures where appropriate.

---

## Research Notes

This lab demonstrates an important access-control principle:

> Client-controlled input must not determine security-sensitive authorization decisions.

The key testing objective is therefore not simply to modify a parameter, but to determine whether the server independently verifies the user's authorization.