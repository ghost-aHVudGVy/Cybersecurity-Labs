# Credential Harvesting with Cloned Website

## Description:

In this lab, I used the Social Engineering Toolkit (SET) in Kali Linux to clone a real website and simulate a credential harvesting attack. This technique is often used by attackers to trick users into entering their login details into a fake but convincing version of a legitimate site.

---

## Objective

- Learn how to clone a website using SET
- Understand how credential harvesting works in real-world attacks
- Capture submitted credentials through a cloned login form

---

## Environment & Tools Used

- **Operating System:** Kali Linux (virtual machine)
- **Tool:** Social Engineering Toolkit (SET)
- **Browser:** Firefox (to test the cloned site)
- **Target Site for Cloning:** `https://www.facebook.com/`

---

## Steps Taken / Summary of Execution

### 🔹 Task 1: Launching SET

- Booted up Kali Linux VM.
- Opened terminal and started SET:
    
    ```bash
    sudo setoolkit
    
    ```
    

### 🔹 Task 2: Selecting Attack Vector

- From the main SET menu, chose: ***Option 2: Website Attack Vectors***

### 🔹 Task 3: Choosing Attack Method

- From the next menu, selected: ***Option 3: Credential Harvester Attack Method***

### 🔹 Task 4: Cloning a Website

- SET prompted for a method — selected: ***Option 2: Site Cloning***
- Entered my local IP address (found using ifconfig).
- When prompted, entered the target URL: https://www.facebook.com/
- SET cloned the site and prepared it for credential capture.

### 🔹 Task 5: Accessing the Cloned Site

- Opened Firefox in Kali and navigated to: `http://my-local-ip`
- Viewed the cloned Facebook login page.
- Entered a test username and password.

### 🔹 Task 6: Capturing Credentials

- Returned to the terminal where SET was running.
- Observed captured POST data.
- Found submitted username and password in cleartext.

---

## Key Learnings / Observations

- Credential harvesting via cloned sites is surprisingly easy with the right tools.
- Users can be easily fooled by realistic-looking clones.
- This technique highlights the importance of phishing awareness and secure browsing practices.
- Tools like SET make it simple to simulate real-world social engineering attacks for learning purposes.

## Screenshots

Screenshots are saved in the screenshots/ folder:

- set_tool_launch.png
- website_attack_vectors.png
- credential_harvester.png
- site_cloner.png
- seting_up_the_cloned_site.png
- captured_results.png

## Challenges Faced / Troubleshooting

- IP Address Confusion: Initially entered the wrong IP address. Fixed by double-checking with ifconfig.

---

## Conclusion

This lab gave me hands-on experience with credential harvesting techniques using a cloned site. I learned how attackers can manipulate users through phishing and social engineering, and how easy it is to simulate such attacks in a controlled environment.
