# 🛡️ DFIR Case Study – DNS Account Compromise & Service Disruption  
### *Digital Forensics & Incident Response Portfolio Project*

**Author:** Herman Franco  
**Date:** February 2025  
**Focus Areas:** DFIR • Memory Forensics • Cloud Security • DNS Analysis • Threat Intelligence

---

# 📌 1. Overview

This repository documents a full **end-to-end DFIR investigation** involving:

- Compromised DNS administrative credentials  
- Unauthorized modification of A and MX records  
- Service disruption to website, email, and cloud infrastructure  
- Cross-platform activity involving GoDaddy, HostGator, Webflow, and Google  
- High-fidelity log analysis  
- IOC extraction & correlation  
- Attack flow reconstruction  
- Executive & technical reporting  

This case study is designed to demonstrate **senior-level DFIR and cloud security skills** for professional roles in:

- Incident Response  
- Security Architecture  
- Cyber Threat Analysis  
- Forensics  
- Cloud Security  

---

# 📁 2. Repository Structure

```
dfir-memory-forensics/
├── analysis/                # Log analysis, correlation, attack hypotheses
├── assets/                  # Images, diagrams, visual evidence
├── diagrams/                # ASCII & architecture diagrams
├── docs/                    # Methodology, case overview
├── evidence/                # Placeholder for memory capture / forensic images
├── ioc/                     # Indicators of Compromise (IPs, domains, hashes)
├── logs/                    # Simulated logs from all affected platforms
├── reports/                 # Final and extended DFIR reports
└── src/                     # Tools/scripts (future expansion)
```

---

# 🔍 3. Executive Summary

On **February 11, 2025**, the administrator account for the company’s DNS provider (GoDaddy) was accessed from an unauthorized foreign IP address originating from **India**. Within minutes, the attacker modified:

- **A record** → website unavailable  
- **MX record** → email delivery failure  

Email queues grew, engineering workflows were disrupted, and communication channels failed.

Correlation between logs, user agents, timestamps, and IOCs strongly indicates:

- **Credential compromise** from the admin workstation  
- **Potential insider involvement** (moderate likelihood)  
- **Intentional sabotage** vs. financial motive  

All services were restored later the same day.

---

# 🧠 4. Attack Diagram (ASCII)

```
[Admin PC (Mexico)]
        |
    credentials stolen
        ↓
[Attacker – India IP]
        |
  valid login to GoDaddy
        |
   DNS A/MX modified
        |
        ↓
    ┌───────────────┐   ┌─────────────────┐
    │ Website Down   │   │ Email Failure   │
    └───────────────┘   └─────────────────┘
```

---

# 📊 5. Timeline Summary

| Time (UTC) | Event |
|------------|------------------------------------------------|
| 09:13 | Legit admin login from Mexico |
| 09:15 | Failed login from India |
| 09:16 | Successful login from India |
| 09:18 | DNS A record tampered |
| 09:19 | DNS MX record modified |
| 09:22–09:24 | Email delivery begins failing |
| ~10:00 | DNS restoration begins |
| ~12:00 | Services fully restored |

Full timeline available in:  
➡ `ioc/timeline-key-events.txt`  
➡ `reports/final-report-extended.md`

---

# 🧩 6. Indicators of Compromise (IOCs)

### IP Addresses
```
103.221.88.14 (Attacker – India)
185.218.126.92 (DNS redirect)
201.180.122.44 (Legitimate admin)
```

### Malicious Domains
```
malicious.mxserver.cc
```

### Compromised Accounts
```
admin@example.com
webmaster@example.com
support@example.com
```

### Hashes
```
sha256: 81b9f7a02e99bfb42d2193adcfe18bbadc79dc8ab87c7dee12391cbc62047195
```

More IOCs in:  
➡ `ioc/`

---

# 🧩 7. Analysis Highlights

### ✔ DNS tampering confirmed  
### ✔ Multiple logs show Indian IP attempts before success  
### ✔ MX redirection caused email outage  
### ✔ Possible insider intel (moderate confidence)  
### ✔ Multi-platform evidence: GoDaddy / HostGator / Webflow / Google  

See full analysis:  
➡ `analysis/`

---

# 🏗️ 8. Architecture Overview

ASCII diagram available in:  
➡ `diagrams/infrastructure-overview.md`

This includes:

- Workstations  
- DNS provider (GoDaddy)  
- Email provider (HostGator)  
- CMS (Webflow)  
- Cloud Identity (Google)  

---

# 📘 9. Reports

### ✔ **Executive DFIR Report (Extended)**  
➡ `reports/final-report-extended.md`

Includes:

- full timeline  
- IOCs  
- MITRE mapping  
- recommendations  
- business impact  
- lessons learned  

---

# 🛠️ 10. Tools & Skills Demonstrated

- log analysis  
- incident reconstruction  
- cloud platform investigation  
- IOC extraction  
- correlation matrixing  
- DFIR documentation  
- ASCII and flow diagramming  
- attacker hypothesis modeling  
- MITRE ATT&CK  
- credential compromise analysis  
- DNS forensics  

---

# 🧭 11. Next Steps (Future Work)

- Add memory dump analysis  
- Add Volatility3 scripts  
- Add Python tools for parsing logs  
- Add YARA rules for credential-theft malware  
- Extend case into a full IR playbook  

---

# ✔️ 12. Contact

If you would like to discuss DFIR work, collaboration, or professional opportunities:

**Herman Franco**  
Cybersecurity | DFIR | Security Engineering  
GitHub: *this profile*  
LinkedIn: (add link)


