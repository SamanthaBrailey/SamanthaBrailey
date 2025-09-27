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

### 1. Kali Linux — Nmap Mini Project
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
## 🔹 Project 2 — Suricata Rule + Wireshark

---

### Step 1 — Start Local HTTP Server
![Step 1](https://i.imgur.com/xyW1mia.png)

---

### Step 2 — Generate HTTP Traffic + Capture in Wireshark
![Step 2a](https://i.imgur.com/DHkGJu9.png)  
![Step 2b](https://i.imgur.com/OXTK2Kh.png)  
![Step 2c](https://i.imgur.com/nPZ5aTY.png)  
![Step 2d](https://i.imgur.com/wokvHwb.png)

---

### Step 3 — Install Suricata IDS
![Step 3](https://i.imgur.com/nPZ5aTY.png)

---

### Step 4 — Create & Run Custom Rule
![Step 4](https://i.imgur.com/S017YSF.png)

---

### Step 5 — Suricata Alert Logged
![Step 5](https://i.imgur.com/tCqM9Fj.png)
