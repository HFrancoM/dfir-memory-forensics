# DNS Tampering Analysis

## Objective
Analyze unauthorized DNS modifications and determine whether they were performed by a malicious actor.

---

## 1. DNS Change Summary
**Unauthorized modifications observed:**

- A record changed:  
  `34.72.18.11 → 185.218.126.92`
- MX record changed:  
  `mail.hostgator.com → malicious.mxserver.cc`

These actions directly caused:
- Website outage  
- Email delivery failure  

---

## 2. Correlation with Authentication Events

| Timestamp | Event |
|----------|------------------------------------------------------|
| 09:15 | Failed login (India) |
| 09:16 | Successful login (India) |
| 09:18 | A record changed |
| 09:19 | MX record changed |

**DNS modifications occur within 2 minutes of Indian login success.**

This is strong evidence of:
- Account compromise  
- Intentional configuration sabotage  

---

## 3. MITRE ATT&CK Mapping

| Tactic | Technique |
|--------|-------------------------------|
| TA0006 – Credential Access | T1078 – Valid Accounts |
| TA0005 – Defense Evasion | T1110 – Brute Force |
| TA0040 – Impact | T1531 – Account Access Removal |
| TA0040 – Impact | T1499 – DoS via Resource Hijacking |

This scenario closely aligns with:
- Credential theft
- Malicious configuration modification
- Service disruption

---

## 4. Technical Impact
- Web presence taken offline  
- Email flow interrupted  
- Business continuity affected  
- Loss of trust between US–Mexico engineering workflow  

DNS sabotage is classified under **high-impact integrity attacks**.

---

## 5. Conclusion
DNS manipulation was executed intentionally by an unauthorized user immediately following a suspicious login event from India. This behavior is inconsistent with misconfiguration and directly attributable to malicious activity.  

