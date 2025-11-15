# Endpoint Risk Summary

## Objective
Summarize endpoint-level risk based on available evidence and identify which systems and users should be prioritized for further investigation.

---

## 1. High-Risk Endpoints and Accounts

### 1.1 Admin Workstation (Mexico)
- **User:** admin@example.com
- **Role:** DNS and email administrator
- **Indicators:**
  - Reports of unusual behavior and suspected remote access.
  - Credentials used from a foreign IP (India).
  - No MFA enabled.
- **Risk:** **High**
- **Recommended Actions:**
  - Full endpoint forensic acquisition (disk + memory).
  - Malware/RAT scan and persistence review.
  - Browser credential store review.
  - Forced credential rotation.

---

### 1.2 Cloud Administrative Consoles
- **Systems:** GoDaddy, HostGator, Webflow, Google
- **Indicators:**
  - Multiple login attempts from unexpected countries.
  - Administrative actions (DNS/MX changes) executed after suspicious login.
- **Risk:** **High**
- **Recommended Actions:**
  - Enable MFA on all admin accounts.
  - Review and restrict admin roles.
  - Implement IP-based alerts for high-privilege logins.

---

### 1.3 Former Employee Accounts
- **Context:**
  - At least one former employee left under hostile conditions.
  - Potential knowledge of architecture and tools.
- **Risk:** **Medium**
- **Recommended Actions:**
  - Audit all active accounts vs HR list.
  - Remove stale accounts and shared credentials.
  - Review password reuse and shared admin accounts.

---

## 2. Overall Endpoint Risk Rating

| Asset / User          | Risk Level | Rationale                                           |
|-----------------------|-----------|-----------------------------------------------------|
| Admin workstation     | High      | Direct credential misuse and suspicious behavior    |
| Cloud admin consoles  | High      | Central control over DNS, email and website         |
| Former employee creds | Medium    | Motive + partial knowledge, but weak direct evidence|

---

## 3. Strategic Recommendations

1. Implement **MFA** on all administrative panels and cloud accounts.  
2. Conduct a **credential hygiene and rotation campaign**.  
3. Establish an **endpoint monitoring baseline** (EDR or logs).  
4. Define a **joiner/mover/leaver process** with strict account revocation.  
5. Introduce **geo-awareness and impossible-travel alerts** for logins.  

