# DFIR Final Report (Extended Version)
## DNS Account Compromise & Service Disruption Incident

**Analyst:** Herman Franco  
**Date:** 2025-02-11  
**Case Type:** Credential Compromise / DNS Tampering / Service Disruption  

---

# 1. Executive Summary

Between 09:13 and 09:19 UTC on February 11, 2025, unauthorized access to the company’s GoDaddy DNS administrative panel resulted in critical DNS modifications leading to:

- **complete website downtime**
- **email delivery failure for all staff**
- **loss of external communication channels**
- **disruption to engineering workflows dependent on cloud storage**

Log correlation strongly indicates that the attacker used **valid account credentials**, logging in from **India** (IP: 103.221.88.14). Shortly after this login, the attacker modified the A and MX records.

Timeline, IOCs, and login patterns suggest a **high-likelihood credential compromise**, possibly supported by:

- a Remote Access Trojan (RAT) on the admin workstation  
- stolen browser-stored credentials  
- insider involvement (moderate likelihood)

Immediate response actions restored service, and the company later migrated email services to Google Workspace. However, the root cause cannot be fully proven due to lack of forensic acquisition.

---

# 2. Business Impact

| Category | Impact |
|----------|---------|
| Website availability | 100% outage during DNS tampering period |
| Email delivery | Failed (MX pointed to rogue domain) |
| Engineering workflow | DWG file exchange interrupted |
| Customer communication | Not possible for several hours |
| Reputational impact | Medium |
| Operational disruption | High |

Estimated total downtime: **~3–5 hours**

---

# 3. Detailed Timeline of Events

| Timestamp (UTC) | Event |
|------------------|------------------------------------------------------------|
| 09:13:21 | Legitimate admin login from Mexico |
| 09:15:49 | Failed login from India |
| 09:16:03 | Successful login from India |
| 09:18:47 | DNS A record modified |
| 09:19:01 | MX record modified |
| 09:22–09:24 | Email delivery begins failing |
| 09:24:03 | HostGator logs show queue growth |
| 09:26:44 | Google account password change from India |
| ~10:00 | Restoration of DNS records begins |
| ~11:00–12:00 | Service gradually returns to normal |
| Later same day | Migration to Google Workspace initiated |

---

# 4. Key Indicators of Compromise (IOCs)

## 4.1 IPs
```
103.221.88.14   (India - attacker)
185.218.126.92  (Rogue A record redirect)
201.180.122.44  (Legitimate admin IP)
```

## 4.2 Malicious Domains
```
malicious.mxserver.cc
```

## 4.3 Compromised Accounts
```
admin@example.com
webmaster@example.com
support@example.com
```

## 4.4 User Agents
- Legitimate: Chrome on Windows  
- Attacker: Firefox on Linux  

---

# 5. Root Cause Assessment

**Most Probable Root Cause:**  
👉 *Credential theft from the admin workstation (High confidence)*

**Additional possibilities:**  
- Insider involvement (Moderate confidence)  
- Password reuse or credential exposure (Moderate confidence)  

Lack of endpoint forensics prevents conclusive determination.

---

# 6. MITRE ATT&CK Mapping

| Tactic | Technique | Description |
|--------|-----------|-------------|
| Credential Access | T1078 Valid Accounts | Attacker used valid admin credentials |
| Initial Access | T1190 Exploit Public-Facing App (possible) | Via host misconfiguration or credential exposure |
| Impact | T1499 Endpoint Denial | Website/email disrupted |
| Defense Evasion | T1110 Brute Force | Observed failed attempts before success |

---

# 7. Diagram of Attack Flow

```
[Admin PC] --> credential theft --> [Attacker (India)]
    |
    --> login --> [GoDaddy Panel] --> DNS tampering
                                   --> MX redirection
                                   --> outage
```

---

# 8. Strategic Recommendations

## Mandatory (High Priority)
1. Enforce MFA across all GoDaddy, email, Webflow, and Google accounts  
2. Rotate all administrative credentials  
3. Disable unused accounts (HR-aligned)  
4. Implement geo-based login alerts  
5. Enable DNS change notifications  
6. Adopt EDR/AV baseline for all endpoints  

## Medium Priority
7. Migrate fully to Google Workspace (completed as mitigation)  
8. Conduct cloud IAM access review  
9. Implement service health monitoring  

## Low Priority
10. Staff training on credential hygiene  
11. Establish formal DFIR process  

---

# 9. Lessons Learned

- Legacy hosting platforms (like HostGator) create fragmentation and risk  
- Lack of MFA on DNS/email systems increases compromise likelihood dramatically  
- DNS tampering is a high-impact attack with quick, severe consequences  
- Cross-cloud visibility is required to detect compromised credentials  
- Administrator accounts require stronger controls than standard users  

---

# 10. Final Conclusion

The attacker successfully authenticated into DNS panel systems using compromised credentials, leading to intentional service disruption. Although direct attribution is not possible, evidence strongly supports credential compromise originating from the administrator workstation.

The organization has taken adequate recovery steps, but additional security investments are required to prevent recurrence, particularly in identity security, endpoint protection, and administrative isolation.

