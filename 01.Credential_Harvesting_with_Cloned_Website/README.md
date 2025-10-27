# Credential Harvesting (Cloned Website)

**Disclaimer:** This lab was performed in a controlled environment on my own virtual machines for educational purposes only. No real-world systems or third-party services were targeted. Do not attempt these techniques outside authorized lab environments.

## Description
This exercise demonstrates how attackers can use cloned websites to harvest credentials (phishing). The goal of the lab is to understand the attack vector, observe how credentials are captured, and learn defensive measures and detection techniques.

## Objectives
- Understand the mechanics of credential-harvesting phishing pages.
- Observe how submitted credentials are captured and stored.
- Learn indicators of compromise and mitigation/detection strategies.

## Environment & Tools
- Kali Linux (VM)
- Social-Engineering toolkit (lab instance)
- Test browser (lab VM)
- Isolated lab network (no internet exposure)

> Note: All activity was performed on isolated, non-production VMs.

## High-level Summary of Actions
- Deployed lab environment and launched a controlled phishing simulation.
- Captured and inspected submitted test credentials within the lab environment.
- Documented observable artefacts (HTTP requests, server logs) and where data was stored in the lab.

[Screenshots](./Screenshots/)

## Findings & Observations
- Cloned pages can appear convincing. Minor visual cues or hosting differences can distinguish them from legitimate sites.
- Captured credential submissions are typically visible in HTTP request bodies or server-side logs when not using HTTPS or when proxying traffic.
- Lab demonstrated how social-engineering + technical setup enables credential capture, underscoring the human element in security.

## Mitigations & Detection (what defenders should do)
- User education and phishing awareness training (recognize suspicious URLs and email indicators).  
- Enforce multi-factor authentication (MFA) on all important accounts to mitigate credential theft.  
- Monitor web server and proxy logs for unusual POST requests or credential-like payloads.  
- Use email and web filtering to block known phishing infrastructure and suspicious domains.  
- Implement HSTS and certificate pinning where possible; educate users about padlock/HTTPS limitations.

## Challenges & Troubleshooting
- Lab networking (local IP routing) required careful configuration — verify your isolated lab network before exercises.  
- Ensure screenshots and logs are redacted before publishing.

## What I learned
- How credential-harvesting attacks function end-to-end in a lab setting.  
- Practical signs of cloned pages and where defenders can look for evidence.  
- Importance of defensive controls (MFA, monitoring, user training).

## References & Further Reading
- OWASP — Phishing and social engineering guidelines  
- Defensive posts on log monitoring and email filtering

