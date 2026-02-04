# Web Application Security Assessment – OWASP Juice Shop

## Overview
This repository documents a hands-on web application security assessment performed against a deliberately vulnerable application (OWASP Juice Shop). The assessment was conducted as part of practical cybersecurity training and was designed to mirror a real-world application security engagement.

The focus of this project was manual testing using Burp Suite to identify, validate, and document vulnerabilities aligned with the OWASP Top 10, with emphasis on understanding exploitability, impact, and remediation rather than automated scanning alone.

---

## Scope and Objectives

**Target Application**
- OWASP Juice Shop (local deployment)

**In Scope**
- Authentication functionality
- User input handling
- Client–server HTTP communication

**Out of Scope**
- Denial-of-Service attacks
- Infrastructure-level attacks

**Objectives**
- Identify OWASP Top 10 vulnerabilities
- Validate exploitability through manual testing
- Analyze security and business impact
- Document findings in a professional assessment format

---

## Tools and Environment
- OWASP Juice Shop (Local)
- Burp Suite Community Edition
- Burp Embedded Browser
- Localhost testing environment

---

## Methodology
The assessment followed a structured application security testing approach:

1. Application mapping and input discovery  
2. Interception and analysis of HTTP requests and responses  
3. Manual manipulation of user-controlled inputs  
4. Validation of exploitability  
5. Impact analysis  
6. Remediation recommendations  

This methodology reflects common practices used in internal security teams and security consulting engagements.

---

## Findings Summary

| Vulnerability | OWASP Category | Severity |
|---------------|---------------|----------|
| SQL Injection (Authentication Bypass) | A03: Injection | Critical |
| Reflected Cross-Site Scripting (XSS) | A07: XSS | High |

---

## Finding 1: SQL Injection – Authentication Bypass

### Description
The login functionality improperly handles user-supplied input, allowing SQL injection. By manipulating the authentication request, it was possible to bypass login controls and gain unauthorized access without valid credentials.

---

### Proof of Concept

The login request was intercepted using Burp Suite and modified with the following payload:

```sql
' OR 1=1--
```
This caused the backend SQL query to evaluate as true, resulting in successful authentication.

---

## Evidence
- Intercepted login request in Burp  
  `screenshots/01_burp_intercept_login_request.png`
- Modified request with SQL injection payload  
  `screenshots/02_sql_injection_payload.png`
- Successful authentication bypass  
  `screenshots/03_sql_injection_successful_login.png`

---

## Impact

- Authentication bypass
- Unauthorized account access
- Potential privilege escalation
- Exposure of sensitive user data

---

## Remediation
- Use parameterized queries (prepared statements)
- Avoid dynamic SQL string construction
- Enforce least-privilege permissions for database accounts

---

## Finding 2: Reflected Cross-Site Scripting (XSS)

### Description

The application reflects unsanitized user input from the search functionality directly into the HTTP response, allowing arbitrary JavaScript execution in the user’s browser.

---

### Proof of Concept
A JavaScript payload was injected into the search parameter:

```html
<script>alert(1)</script>
```
The payload executed successfully, confirming a reflected XSS vulnerability.

## Evidence
- Intercepted search request in Burp
  `screenshots/04_burp_intercept_search_request.png`
- XSS payload injected into request
  `screenshots/05_xss_payload_in_request.png`
- JavaScript execution in browser
  `screenshots/06_xss_alert_execution.png`

## Impact
- Session hijacking
- Credential theft
- Malicious redirection
- Client-side compromise

## Remediation
- Apply proper output encoding based on context
- Validate and sanitize user input
- Implement a Content Security Policy (CSP)

## Key Takeaways
- Manual testing is critical for validating real exploitability
- Automated tools assist detection but require human validation
- Understanding HTTP request flows is essential for application security
- Clear documentation is a core part of security work

## Disclaimer
This assessment was conducted strictly in a controlled lab environment using an intentionally vulnerable application. No production systems or real-world targets were tested.
