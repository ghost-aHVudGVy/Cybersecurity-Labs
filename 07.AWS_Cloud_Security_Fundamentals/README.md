# AWS Cloud Security Fundamentals Lab

## Overview

This project documents an entry-level cloud security implementation performed in an AWS Free Tier environment.  
The goal of this lab was to apply foundational AWS security best practices aligned with real-world Cloud / SecOps responsibilities.

The lab focuses on identity security, network security, logging and monitoring, and identifying common cloud misconfigurations, following AWS and industry best practices.

All activities were conducted in a controlled personal AWS account for learning purposes only.

---

## Objectives

- Understand and apply the AWS Shared Responsibility Model
- Secure the AWS root account
- Implement IAM users, roles, policies, and MFA
- Secure network access using security groups
- Enable and validate centralized logging with AWS CloudTrail
- Identify and remediate common AWS security misconfigurations
- Document findings in a professional security-focused format

---

## AWS Shared Responsibility Model

AWS is responsible for:
- Physical data centers
- Hardware and infrastructure
- Underlying cloud platform security

Customer responsibilities include:
- Identity and Access Management (IAM)
- Network configurations
- Logging and monitoring
- Data protection
- Application and OS security

This lab focuses entirely on customer-side responsibilities.

---

## Root Account Security

### Actions Taken

- Enabled Multi-Factor Authentication (MFA) on the AWS root account
- Verified root account is no longer used for daily operations

### Security Impact

- Reduces risk of total account compromise
- Aligns with AWS security best practices

### Evidence

- screenshots/01_root_mfa_enabled.png

---

## Identity and Access Management (IAM)

### IAM User Creation

Created a dedicated IAM user for security operations:

- Username: security-analyst
- Console access enabled
- Forced password reset on first login
- Programmatic access disabled

### Permissions Applied

- Attached AWS managed policy: SecurityAudit
- No administrative privileges granted

This follows the principle of least privilege.

### MFA Enforcement

- MFA enabled for the IAM user
- Prevents unauthorized access even if credentials are compromised

### Evidence

- screenshots/02_iam_user_created.png
- screenshots/03_iam_user_policy_attached.png
- screenshots/04_iam_user_mfa_enabled.png

---

## IAM Role Implementation

### Purpose

Created an IAM role to allow EC2 instances to interact securely with AWS services without hardcoded credentials.

### Role Details

- Role name: ec2-monitoring-role
- Trusted entity: EC2
- Attached policy: CloudWatchAgentServerPolicy

### Security Impact

- Eliminates static credentials
- Enables secure service-to-service authentication

### Evidence

- screenshots/05_iam_role_created.png

---

## Network Security (Security Groups)

### Default Security Group Review

Reviewed default security group configurations to identify potential risks:
- Open outbound traffic
- Self-referencing inbound rules

### Secure Security Group Creation

Created a hardened security group for a web server:

Inbound rules:
- HTTP (80): Allowed (documented exposure)
- SSH (22): Restricted to administrator IP only

Outbound rules:
- Default allowed (documented reasoning)

### Security Impact

- Reduces attack surface
- Prevents unauthorized remote access

### Evidence

- screenshots/06_security_group_rules.png

---

## Logging and Monitoring (AWS CloudTrail)

### CloudTrail Configuration

- Created a multi-region CloudTrail
- Enabled management events (read and write)
- Logs stored in a dedicated S3 bucket
- Log file validation enabled

### Validation

- Generated IAM activity
- Verified events appeared in CloudTrail event history

### Security Impact

- Enables forensic investigations
- Provides visibility into account activity
- Meets compliance and audit expectations

### Evidence

- screenshots/07_cloudtrail_enabled.png
- screenshots/08_cloudtrail_event_history.png

---

## Misconfiguration Identification and Remediation

### Identified Issues

- Potential overly permissive security group rules
- Risk of exposed SSH access

### Remediation

- Restricted SSH access from 0.0.0.0/0 to a specific administrator IP
- Verified rule changes were applied successfully

### Security Impact

- Prevents brute-force and unauthorized access attempts
- Demonstrates proactive risk management

### Evidence

- screenshots/09_security_group_before_fix.png
- screenshots/10_security_group_after_fix.png

---

## Key Takeaways

- Cloud security is primarily the customer’s responsibility
- IAM misconfigurations are a leading cause of cloud breaches
- MFA is critical for both root and IAM users
- Security groups act as the first line of network defense
- Logging and monitoring are essential for detection and response
- Identifying and fixing misconfigurations is a core security skill

---

## Disclaimer

This project was conducted in a personal AWS Free Tier account strictly for educational purposes.  
No production systems, customer data, or real-world environments were involved.

---

## Repository Structure

```
07.AWS_Cloud_Security_Fundamentals/
├── README.md
└── screenshots/
    ├── 01_root_mfa_enabled.png
    ├── 02_iam_user_created.png
    ├── 03_iam_user_policy_attached.png
    ├── 04_iam_user_mfa_enabled.png
    ├── 05_iam_role_created.png
    ├── 06_security_group_rules.png
    ├── 07_cloudtrail_enabled.png
    ├── 08_cloudtrail_event_history.png
    ├── 09_security_group_before_fix.png
    └── 10_security_group_after_fix.png
```
