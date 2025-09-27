# Welcome to My GitHub Portfolio 👋

Hi, I’m Samantha Brailey.  
I have a **Bachelor’s degree in Cybersecurity** and I’m currently working on my **Master’s in Cyber Operations**.  
This portfolio is where I document my hands-on projects, labs, and research in cybersecurity.

---

## 🔹 About Me
- 🎓 B.S. in Cybersecurity  
- 📚 Currently pursuing M.S. in Cyber Operations  
- 🛡️ Interests: SOC operations, incident response, penetration testing, and security automation  
- 💡 Goal: Build a career in cyber operations and threat detection  

---

## 🔹 My Projects

### 1. Kali Linux — Nmap Mini Project https://github.com/SamanthaBrailey/Kali-Linux-Nmap-Mini-Project/blob/main/README.md
**Goal:** Demonstrate basic network reconnaissance skills used in cyber operations (SOC / Incident Response).

---

#### Step 1 — Find target IP
Command:
![Target IP](https://i.imgur.com/VClcNVR.png)

---

#### Step 2 — Host discovery
Command:
![nmap host discovery](https://i.imgur.com/HSYAYNe.png)

---

#### Step 3 — Service/version scan
Command:
- Saved output: `nmap_sV_results.txt`  

![nmap service scan](https://i.imgur.com/1eZpuL8.png)

---

#### Analysis
- All 1000 common TCP ports were closed.  
- This shows the host is live but not running any exposed services.  
- In a SOC context, this could indicate:  
  - A hardened endpoint with services firewalled/disabled.  
  - A system not intended to serve network apps.  
  - Or a fresh VM with no services installed.  

📄 Full analysis in [ANALYSIS.md](ANALYSIS.md)

---

*(More projects will be added soon — cloud security labs, packet analysis, password auditing, etc.)*
# 🔹 Project 2 — Suricata Rule + Wireshark

---

## Step 1 — Start Local HTTP Server
![Step 1](https://i.imgur.com/xyW1mia.png)

- A Python HTTP server was started on port `8000` to generate traffic.  
- This creates a controlled environment to observe how requests and responses look in Wireshark.  

---

## Step 2 — Generate HTTP Traffic + Capture in Wireshark
During this step, I generated HTTP requests to the local server and captured them in Wireshark. The goal was to prove that plaintext HTTP traffic can be observed and analyzed before applying Suricata rules.

### 🔹 Screenshot 1 — Wireshark Initial Capture
![Step 2a](https://i.imgur.com/DHkGJu9.png)  
- Shows traffic on `eth0`, including TLS and ARP.  
- Confirms Wireshark is actively capturing live packets.  

### 🔹 Screenshot 2 — Sending HTTP Request
![Step 2b](https://i.imgur.com/OXTK2Kh.png)  
- Used `curl` to request `/secret_admin_area`.  
- Server responded with `404 Not Found`.  
- Even though the page doesn’t exist, the attempt generates valid HTTP traffic.  

### 🔹 Screenshot 3 — Loopback Capture in Wireshark
![Step 2c](https://i.imgur.com/nPZ5aTY.png)  
- Wireshark filtered on `http` and displayed clear GET/HEAD requests between `127.0.0.1`.  
- Demonstrates how local traffic is visible at the packet level.  

### 🔹 Screenshot 4 — Packet Details
![Step 2d](https://i.imgur.com/wokvHwb.png)  
- Shows a detailed breakdown of the `HEAD /secret_admin_area` request.  
- Highlights the requested URI, proving sensitive paths are exposed in plaintext over HTTP.  

**➡ Why it matters:**  
- This step shows how unencrypted HTTP requests can be inspected directly.  
- Analysts can identify suspicious paths (`/secret_admin_area`) or unusual traffic patterns.  
- This provides the baseline for creating Suricata rules to detect and alert on similar activity.  

---

## Step 3 — Install Suricata IDS
![Step 3](https://i.imgur.com/nPZ5aTY.png)

- Suricata was installed to act as an Intrusion Detection System (IDS).  
- It will analyze the same traffic Wireshark sees, but with rule-based detection.  

---

## Step 4 — Create & Run Custom Rule
![Step 4](https://i.imgur.com/S017YSF.png)

- A Suricata rule was written to detect requests to `/secret_admin_area`.  
- This simulates how analysts create custom signatures for suspicious or sensitive activity.  

---

## Step 5 — Suricata Alert Logged
![Step 5](https://i.imgur.com/tCqM9Fj.png)

- Suricata successfully logged an alert when the request was made.  
- Confirms that the rule worked and the suspicious HTTP traffic was detected.  

---

## 📄 Notes
- Wireshark provides **visibility** into raw packets.  
- Suricata adds **detection** and alerting capability.  
- Together, they replicate a SOC workflow for analyzing and monitoring traffic.  
## 📌 Suricata Rule Used
```suricata
alert http any any -> 127.0.0.1 8000 (
    msg:"Alert: Access attempt to /secret_admin_area";
    flow:to_server,established;
    http.uri; content:"/secret_admin_area"; nocase;
    classtype:web-application-activity;
    sid:1000001; rev:1;)
