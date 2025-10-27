# WHOIS & Subdomain Recon (Recon-ng)

**Disclaimer:** All recon was performed for educational purposes in a controlled lab environment and against publicly available information. Do not perform reconnaissance against systems you do not own or do not have explicit permission to test. Use public test targets or obtain written authorization before attempting any active probing.

## Description  
This lab demonstrates Open-Source Intelligence (OSINT) techniques using Recon-ng to collect WHOIS information and discover subdomains for a target domain. The goal is to understand how publicly available domain metadata and subdomain enumeration can reveal an organization’s digital footprint.

---

## Objectives
- Automate WHOIS data collection and parsing.  
- Discover subdomains and resolve associated IP addresses.  
- Understand how domain metadata supports further reconnaissance and defensive analysis.

---

## Environment & Tools
- Host OS: Kali Linux (virtual machine)  
- Tool: Recon-ng (framework for automated OSINT collection)  
- Notes: Operations were limited to passive, publicly available sources. No active exploitation or unauthorized access was attempted.

---

## High-level Summary of Actions
- Launched Recon-ng and created a dedicated workspace for the engagement.  
- Loaded modules to collect WHOIS records and passive DNS / subdomain data from public sources.  
- Executed modules to capture available metadata (registration/registrant fields) and to aggregate discovered subdomains and IP addresses.  
- Exported results and saved screenshots and output for documentation.

[Screenshots](./Screenshots)

---

## Key Findings
- WHOIS records can reveal registrar information, registration/expiration dates, and sometimes administrative contacts (subject to privacy protection services).  
- Subdomain enumeration often uncovers additional assets (e.g., staging, dev, or legacy systems) that may not be obvious from the main site.  
- Passive sources (certificate transparency logs, public subdomain lists) frequently yield useful domain names that warrant further defensive attention.

---

## Defensive / Mitigation Notes
- Monitor certificate transparency logs (CRT) and passive DNS for unexpected subdomains or certificate issuance.  
- Harden exposed services on discovered subdomains and verify authentication controls.  
- Review WHOIS / registrar data periodically and ensure contact info and registrar security (use registrar lock, 2FA).  
- Implement DNS monitoring and alerting for newly created subdomains or DNS record changes.  
- Use asset inventory to map authorized subdomains and detect out-of-band or forgotten assets.

---

## Challenges & Notes
- Public WHOIS data may be limited or privacy-protected (WHOIS privacy services can hide contact info).  
- Different sources return different results. Aggregation improves coverage.  
- Always verify discovered assets with owners where appropriate before any further action.

---

## What I learned / Takeaways
- Recon-ng provides an efficient framework to automate OSINT collection and module chaining.  
- Passive reconnaissance uncovers a domain’s external footprint and helps defenders prioritize monitoring and hardening efforts.  
- Effective recon requires combining multiple data sources and validating findings to reduce false positives.
