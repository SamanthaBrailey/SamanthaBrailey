# Nmap Mini Project — Analysis

**Target IP:** 10.0.2.15  
**Date:** 2025-09-27  

---

## Summary of Findings
I used Nmap to perform reconnaissance on my target VM. The process had 3 steps:

- **Step 1: Find the target IP**  
  Command:  
Result: The target machine’s IP address was identified as `10.0.2.15`.  

- **Step 2: Host discovery**  
Command:  
Result: The host responded, confirming it was live and reachable.  

- **Step 3: Service/version scan**  
Command:  
Result: All 1000 common TCP ports were closed or reset. No open services were detected.  

---

## Interpretation (Cyber Ops Perspective)
- The host is online but does not expose any open services.  
- In a SOC or incident response scenario, this could indicate:
- The endpoint is **hardened** (firewall or security settings block access).  
- The system is **not configured** to provide services (e.g., a workstation).  
- Or it is a **fresh VM** with no active network services.  

---

## Next Steps (If This Were a SOC Task)
1. Verify host role against asset inventory.  
2. Review firewall/endpoint logs to understand why all ports are closed.  
3. If unexpected, escalate to confirm whether this restriction was intentional or misconfiguration.  

---

## Reflection
This mini-project demonstrates:
- Using Nmap in **3 logical steps** (IP discovery → host discovery → service scan).  
- How to capture and document results with screenshots and saved output.  
- Interpreting even a “no open ports” result in a SOC/cyber operations context.  
