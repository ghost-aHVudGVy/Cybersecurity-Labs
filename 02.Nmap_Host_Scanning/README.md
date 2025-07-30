# Nmap Host Scanning Lab

## Description:  
In this lab, I used Nmap to scan a remote host and learn how to identify open ports, running services, and operating system details.

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
  ```bash
  nmap scanme.nmap.org
This scanned the top 1000 ports and showed 4 open ports with basic service info.

### 🔹 Task 2: Advanced Scan with Root Access
Tried running:
    ```bash
    sudo nmap -v -sT -sV -O scanme.nmap.org

***This scan revealed:*** 
1. **Open Ports (TCP):**
    - **22 (SSH)** – Blocked/restricted (**`tcpwrapped`**).
    - **80 (HTTP), 443 (HTTPS), 8080 (HTTP-alt)** – Web services running.
2. **Closed/Filtered Ports:**
    - **53 (DNS)** – Closed.
    - **995 others** – Filtered (likely firewalled).
3. **OS Detection:**
    - Likely **VirtualBox/QEMU** (virtual machine).
    - No exact OS match (limited scan conditions).
4. **Key Insight:**
    - **No service versions** detected (**`tcpwrapped`** suggests restricted access).

### 🔹 Task 3: Exploring Other Scan Flags
Tried other scan options like: `sudo nmap -A scanme.nmap.org`

***This scan revealed more details:*** 
1. **Open Ports & Services**:
    - **22/tcp (SSH)**
        - Exposed SSH host keys (DSA, RSA, ECDSA, ED25519).
        - Indicates SSH is running but may be firewrapped (**`tcpwrapped`**).
    - **80/tcp (HTTP)**
        - **Web server**: Apache/2.4.7 (Ubuntu).
        - **Title**: *"Go ahead and ScanMe!"* (confirms it’s Nmap’s test server).
        - **Favicon**: Nmap Project logo.
    - **443/tcp (HTTPS)** & **8080/tcp (HTTP-alt)**
        - Open but no additional details (likely similar to port 80).
2. **Closed/Filtered**:
    - **53/tcp (DNS)** → Closed (no DNS service on TCP).
    - **995 other ports** → Filtered (no response, likely firewalled).
3. **OS & Network**:
    - **Likely OS**: Virtualized (Oracle VirtualBox/QEMU).
    - **Network Distance**: 1 hop (you’re close to the server, possibly same ISP).
4. **Traceroute**:
    - Direct connection (no intermediate hops).

## **What’s New vs. Previous Scan?**

- **SSH Host Keys** (useful for fingerprinting).
- **HTTP Details** (server version, page title, favicon).
- **Traceroute Confirmation** (no middlemen).

## **Bottom Line:**

This scan reveals:

- A **Ubuntu Apache server** running on port 80 with a test page.
- **SSH is available** (but may be restricted).
- The host is likely a **virtual machine** (VirtualBox/QEMU).

---

## Key Learnings / Observations
- Nmap is an essential tool for network reconnaissance.
- Even a simple scan reveals useful information like open ports and services.
- Advanced scans require root access but give deeper insights, including service versions and OS guesses.
- The ***-A*** flag combines multiple scan techniques and gives a more detailed picture of the target.

## Screenshots
Screenshots are saved in the screenshots/ folder:

- [basic_scan.png](./Screenshots/01.basic_scan.png)
- [aggressive_scan.png](./Screenshots/02.aggressive_scan.png)

## Challenges Faced / Troubleshooting
- Root Access Needed: Couldn’t perform advanced scans without sudo. Fixed by rerunning the command with sudo.
- Firewall Consideration: Some scan results may vary if a firewall is present. In this case, the target was intentionally left open for scanning.

---

## Conclusion
This lab gave me hands-on experience using Nmap for both basic and advanced host scanning. I learned how to extract useful information about a target system. It also helped me better understand how attackers gather intelligence, which is key for defending systems effectively.
