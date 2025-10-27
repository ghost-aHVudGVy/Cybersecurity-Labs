# Lab: Nmap Host Scanning

**Description**  
This lab demonstrates host discovery and service enumeration using Nmap. The aim is to learn how to perform basic and more advanced scans, interpret results, and understand what information an attacker or defender can extract from network scanning.

**Disclaimer / Legal**  
All scanning was performed against `scanme.nmap.org`, a public test target provided by the Nmap project for learning purposes. Do **not** scan systems you do not own or do not have explicit permission to test. Always use an isolated lab or authorized targets.

---

## Objectives
- Learn basic and advanced Nmap scan types and options.  
- Interpret open ports, running services, and OS/service fingerprinting results.  
- Understand limitations of scanning (firewalls, tcpwrapped services, rate-limiting).

---

## Environment & Tools
- Host OS: Kali Linux (virtual machine)  
- Tool: Nmap (pre-installed in Kali)  
- Target: `scanme.nmap.org` (public test host)  
- Notes: Lab executed on an isolated VM network; no production systems were targeted.

---

## High-level Summary of Actions
- Performed a basic TCP scan to identify common open ports and services.  
- Performed a more detailed scan (service/version detection and OS fingerprinting) to gather additional information where permitted by the target.  
- Compared results across scan variants to observe differences and the effect of filtering/firewalls.
[Screenshots](./Screenshots/)

---

## Key Findings
- **Open ports identified (example):** 22/tcp (SSH), 80/tcp (HTTP), 443/tcp (HTTPS), 8080/tcp (HTTP-alt).  
- **Service details:** Web server identified on port 80 (Apache) with a test page confirming the host purpose. Service version detection may be limited by protections such as `tcpwrapped`.  
- **OS fingerprinting:** Results suggested a virtualized host (VirtualBox/QEMU); exact OS matching can be unreliable under some conditions.  
- **Network traversal:** Traceroute-like output indicated a short network path (1 hop), consistent with a nearby test host.

---

## Defensive / Mitigation Notes (what defenders should do)
- Treat all unexpected external scanning as suspicious. Correlate with other telemetry (IDS/IPS, firewall logs).  
- Monitor for unusual or repetitive port probing and rate-limit or block offending IPs.  
- Use service banner hardening and minimize information exposed in service responses.  
- Employ network segmentation and firewall rules to limit public exposure of management services (SSH, RDP, etc.).  
- Encourage multi-factor authentication (MFA) to mitigate credential theft if services are discovered.  
- Log and alert on suspicious service/version changes or increased scanning activity.
- 
---

## Challenges & Troubleshooting
- **Root permissions required for some advanced options:** resolved by using elevated privileges in the lab VM.  
- **Firewall/IpTables effects:** some ports showed as filtered; results can vary based on network path and filtering.

---

## What I learned / Takeaways
- Nmap is a powerful reconnaissance tool: even basic scans reveal useful info for both attackers and defenders.  
- Advanced flags (service/version and OS detection) provide more detail but may be limited by protections or network factors.  
- Defensive teams should monitor for scanning activity and harden publicly accessible services.

---

## References & Further Reading
- Nmap documentation: https://nmap.org/book/  
- Nmap project (scanme info): https://nmap.org/scanme/  
- OWASP testing and defensive resources

