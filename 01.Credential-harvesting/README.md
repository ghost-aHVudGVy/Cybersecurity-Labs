# Lab: Credential Harvesting via Cloned Website

## Objective

Harvest user credentials using a cloned version of a legitimate website hosted locally.

## Purpose

Demonstrate how attackers use cloned websites to conduct phishing and capture sensitive user input, such as usernames and passwords, without the target's awareness.

## Tools & Environment

- **Operating System**: Kali Linux (Virtual Machine)
- **Tool**: Social Engineering Toolkit (SET)
- **Browser**: Firefox
- **Target Site (for cloning)**: https://www.instagram.com *(used for educational purposes only)*

## Lab Topology

                    Attacker (Kali Linux VM)
                                |
                         [Cloned Website]
                                |
                 Victim (Web Browser accessing local IP)

---

## Walkthrough

**Step 1: Launch SET**

* sudo setoolkit

* Select 2) Website Attack Vectors

- Select 3) Credential Harvester Attack Method

**Step 2: Clone a Website**
- Choose 2) Site Cloner

- Enter your local IP address (found using ifconfig)

- Enter the URL to clone: https://www.instagram.com/

**Step 3: Access the Cloned Site**
- Open Firefox on Kali Linux

- Visit your IP address in the browser (e.g. http://192.168.1.10)

- The cloned Instagram login page should appear

- Enter fake credentials (e.g. testuser / testpass)

**Step 4: View Captured Credentials**
- Go back to the terminal where SET is running

- Look for the POST data showing captured credentials:

username=testuser
password=testpass

## Screenshots
[Screenshots](https://github.com/ghost-aHVudGVy/Cybersecurity-Labs/blob/main/01.Credential-harvesting/Screenshots)

## What I Learned
- How phishing attacks can be carried out using cloned websites

- The role of Social Engineering Toolkit (SET) in simulating real-world attacks

- The importance of verifying URLs and HTTPS certificates

- Why user awareness is key in preventing social engineering attacks

## Disclaimer
This lab was conducted in a secure, isolated environment for educational purposes only. Never attempt these techniques on unauthorized systems or networks.

## Files Included

| File/Folder    | Description                     |
| -------------- | ------------------------------- |
| `README.md`    | Lab documentation               |
| `screenshots/` | Visual references for key steps |
| `notes.txt`    | Notes and observations |
