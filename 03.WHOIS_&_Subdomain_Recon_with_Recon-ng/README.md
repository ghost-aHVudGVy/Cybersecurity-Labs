# WHOIS & Subdomain Recon with Recon-ng

## Description:  
In this lab, I used Recon-ng to gather WHOIS and subdomain information about a target domain. This kind of information can help identify ownership details, infrastructure, and potential weaknesses in an organization’s web presence.

---

## Objective

- Use Recon-ng to automate WHOIS data collection
- Discover subdomains and associated IP addresses
- Understand how domain-related metadata can be used for further reconnaissance

---

## Environment & Tools Used

- **Operating System:** Kali Linux (virtual machine)
- **Tool:** Recon-ng
- **Target Domain:** `facebook.com`

---

## Steps Taken / Summary of Execution

### 🔹 Task 1: Launching Recon-ng
- Booted Kali Linux and opened terminal.
- Started Recon-ng:
  ```bash
  recon-ng
### 🔹 Task 2: Creating a Workspace
- Created a new workspace for this project:
    ```bash
    workspaces create whois_recon
### 🔹 Task 3: Collecting WHOIS Information
- Searched for WHOIS modules:
    ```bash
    marketplace search whois
- Installed the desired module:
    ```bash
    marketplace install recon/domains-contacts/whois_pocs
- Set the domain source:
    ```bash
    options set SOURCE facebook.com
- Loaded the module:
    ```bash
    modules load recon/domains-contacts/whois_pocs
(Optional) Viewed module info:
    ```bash
    info
- Ran the module to gather WHOIS data:
    ```bash
    run
- Output: Contact names, emails, phone numbers, and registration details for facebook.com were retrieved and stored.

### 🔹 Task 4: Discovering Subdomains with HackerTarget
-Exited previous module:
    ```bash
    back
- Searched for HackerTarget module:
    ```bash
    marketplace search hackertarget
- Installed the subdomain discovery module:
    ```bash
    marketplace install recon/domains-hosts/hackertarget
- Loaded the module:
    ```bash
    modules load recon/domains-hosts/hackertarget
- Set the source domain:
    ```bash
    options set SOURCE facebook.com
- (Optional) Viewed module info:
    ```bash
    info
- Ran the module:
    ```bash
    run
- Output: A list of discovered subdomains and their corresponding IPv4 addresses was returned.

## Key Learnings / Observations
- Recon-ng helps streamline open-source intelligence (OSINT) gathering.
- WHOIS data reveals domain ownership, contact info, and registration timelines.
- Subdomains often reveal additional infrastructure that might be more vulnerable than the main domain.
- Framework-based recon is more efficient than running individual tools manually.

## Screenshots
Screenshots are saved in the screenshots/ folder:
- [01.run_recon-ng.png](./Screenshots/01.run_recon-ng.png)
- [02.creating_whois_workstation.png](./Screenshots/02.creating_whois_workstation.png)
- [03.instaling_search_whois.png](./Screenshots/03.instaling_search_whois.png)
- [04.set_source.png](./Screenshots/04.set_source.png)
- [05.run_whois.png](./Screenshots/05.run_whois.png)
- [06.instaling_hackertarget.png](./Screenshots/06.instaling_hackertarget.png)
- [07.1.runing_hackertarget.png](./07.1.runing_hackertarget.png)
- [07.2.summery.png](./Screenshots/07.2.summery.png)

## Challenges Faced / Troubleshooting
- No challenges

---

## Conclusion
This lab provided practical experience in collecting WHOIS and subdomain data using Recon-ng. These techniques are commonly used to map a target’s digital footprint. It also demonstrated how publicly available information can be used to uncover potential entry points during a real-world assessment.
