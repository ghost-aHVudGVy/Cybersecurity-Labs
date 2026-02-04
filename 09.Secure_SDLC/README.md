# Secure Software Development Lifecycle (Secure SDLC)
### Application Security Integration

---

## Overview

This project demonstrates how security can be integrated into each phase of the Software Development Lifecycle (SDLC) for a small web application.

The goal of this lab was to understand how application security works **in collaboration with development teams**, focusing on preventing vulnerabilities early, reducing overall risk, and supporting secure software delivery without slowing development.

This assessment reflects a real-world AppSec and DevSecOps mindset rather than a purely theoretical approach.

---

## Scenario Description

**Target Application**
- Small web application
- User and administrator roles
- Authentication and authorization required
- Backend API with relational database
- CI/CD pipeline used for deployment

**Role**
- Embedded Security Engineer collaborating with developers throughout the SDLC

---

## SDLC Phase 1: Requirements & Planning

### Security Focus

Security considerations were introduced during the planning phase to ensure risks were addressed before development began.

### Key Activities
- Identified sensitive data and access requirements
- Defined authentication and authorization expectations
- Established baseline security requirements

### Security Requirements Identified
- Authentication required for sensitive actions
- Role separation between users and administrators
- Secure password storage
- Logging for authentication-related events

### Why This Matters
Addressing security during planning reduces the likelihood of architectural flaws that are expensive and difficult to fix later.

---

## SDLC Phase 2: Design

### Security Focus

The application design was reviewed to identify trust boundaries, attack paths, and potential security weaknesses.

### Key Activities
- Reviewed application architecture
- Identified trust boundaries between users, application, and backend systems
- Performed lightweight threat modeling
- Identified risks such as authentication bypass, injection attacks, and privilege escalation

### Recommended Design Controls
- Centralized authentication
- Role-Based Access Control (RBAC)
- Least-privilege database access
- Input validation at the API layer

---

## SDLC Phase 3: Development

### Security Focus

Secure coding practices were emphasized during development to prevent common vulnerabilities.

### Key Activities
- Mapped common vulnerabilities to insecure coding patterns
- Provided secure coding guidance to developers
- Encouraged security-focused code reviews

### Vulnerabilities Addressed
- SQL Injection
- Cross-Site Scripting (XSS)
- Authorization bypass
- Insecure password handling

### Secure Development Practices
- Parameterized queries
- Proper output encoding
- Centralized authorization checks
- Secure password hashing

---

## SDLC Phase 4: Testing

### Security Focus

Security testing was used to validate the application before deployment.

### Testing Activities
- Static Application Security Testing (SAST)
- Dynamic Application Security Testing (DAST)
- Manual validation of findings

### Key Principles
- Automated tools assist detection
- Manual testing confirms exploitability
- Findings were prioritized based on impact and risk

---

## SDLC Phase 5: CI/CD Integration (DevSecOps)

### Security Focus

Security controls were integrated into the CI/CD pipeline to ensure continuous assessment.

### CI/CD Security Controls
- Automated SAST on code commits
- Dependency vulnerability scanning
- DAST scans on deployed environments

### Pipeline Enforcement
- Critical findings block builds
- Medium-risk findings generate warnings
- Fast feedback provided to developers

---

## SDLC Phase 6: Deployment & Operations

### Security Focus

Security responsibilities continued after deployment.

### Key Activities
- Verified secure configuration
- Ensured HTTPS was enforced
- Confirmed secrets were not hardcoded
- Enabled logging and monitoring for security events

### Operational Security
- Authentication events monitored
- Errors and anomalies logged
- Incident readiness considered

---

## Communicating Security Findings to Developers

### Approach

Security findings were communicated clearly and constructively to developers.

### Best Practices
- Explained technical issues in practical terms
- Focused on impact and remediation
- Avoided blame or blocking language

### Example
Instead of stating that something is insecure, findings were explained with context and recommended fixes.

---

## Key Takeaways

- Security is most effective when introduced early
- Collaboration with developers is critical
- Automated testing must be combined with human validation
- Clear communication is essential for successful AppSec programs
- Secure SDLC reduces long-term security risk and cost

---

## Disclaimer

This Secure SDLC exercise was conducted in a controlled lab environment for educational and portfolio purposes. No production systems or real-world applications were tested.

