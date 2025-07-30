# Nmap Host Scanning Lab

## Description:  
In this lab, I used Nmap to scan a remote host and learn how to identify open ports, running services, and operating system details. Nmap is a powerful tool used by both system administrators and attackers to gather information about networked devices.

---

## Objective

- Understand how to run basic and advanced Nmap scans
- Learn how to interpret scan results
- Identify ports, services, and OS information from a target host

---

## Environment & Tools Used

- **Operating System:** Kali Linux (running in a virtual machine)
- **Tool:** Nmap (pre-installed in Kali)
- **Target Host:** scanme.nmap.org (safe practice site provided by Nmap)

---

## Steps Taken / Summary of Execution

### 🔹 Task 1: Basic Scan
- Opened the terminal in Kali and ran:
  
bash
  nmap scanme.nmap.org
This scanned the top 1000 ports and showed 4 open ports with basic service info.

### 🔹 Task 2: Advanced Scan with Root Access
Tried running: `nmap -v -sT -sV -O scanme.nmap.org`
but was prompted for root access.

- Re-ran using sudo:
bash
  sudo nmap -v -sT -sV -O scanme.nmap.org

***This scan revealed:*** 
- Versions of services running on each open port
- Operating system details of the target host

### 🔹 Task 3: Exploring Other Scan Flags
Tried other scan options like: sudo nmap -A scanme.nmap.org and more

---

## Key Learnings / Observations
- Nmap is an essential tool for network reconnaissance.
- Even a simple scan reveals useful information like open ports and services.
- Advanced scans require root access but give deeper insights, including service versions and OS guesses.
- The ***-A*** flag combines multiple scan techniques and gives a full picture of the target.

## Screenshots
Screenshots are saved in the screenshots/ folder:

- basic_scan_result.png
- advanced_scan_with_sudo.png
- scan_with_a_flag.png

## Challenges Faced / Troubleshooting
- Root Access Needed: Couldn’t perform advanced scans without sudo. Fixed by rerunning the command with sudo.
- Firewall Consideration: Some scan results may vary if a firewall is present. In this case, the target was intentionally left open for scanning.

---

## Conclusion
This lab gave me hands-on experience using Nmap for both basic and advanced host scanning. I learned how to extract useful information about a target system. It also helped me better understand how attackers gather intelligence, which is key for defending systems effectively.
