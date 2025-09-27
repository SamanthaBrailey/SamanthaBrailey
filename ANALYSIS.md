# Nmap Mini Project — Analysis

**Target IP:** 10.0.2.15  
**Date:** 2025-09-27  

---

## Summary of Findings
I used Nmap to perform reconnaissance on my target VM.  

- **Step 1:** Verified the host was up using:
Result: Host responded, confirming it was live.  

- **Step 2:** Ran a service/version scan using:
Result: All 1000 common TCP ports were closed or reset.  

---

## Interpretation (Cyber Ops Perspective)
- The host is reachable on the network but does not expose any open services.  
- In a SOC or incident response scenario, this could mean:
- The endpoint is **hardened** (firewalled, patched, or service-restricted).  
- The system is **not configured to provide network services** (e.g., a workstation or clean VM).  
- Or it may be a **fresh machine with no services installed** yet.  

---

## Next Steps (If This Were a SOC Task)
1. **Verify host role** — check asset inventory to confirm if this system should/should not expose services.  
2. **Check firewall or endpoint logs** to see why ports are closed.  
3. **If unexpected**, escalate to determine if the machine was intentionally restricted or if a configuration error occurred.  

---

## Reflection
This project demonstrates how basic reconnaissance is performed in Kali Linux using Nmap, and how results are documented for cyber operations. Even a result of “all ports closed” provides valuable context — it shows the analyst’s ability to:
- Verify host availability  
- Capture results in text and screenshots  
- Interpret findings in a security operations context  
