# Attack Path Hypothesis

## Objective
Propose the most likely attack path based on available evidence, timing, and access patterns.

---

## 1. Potential Attack Paths

### Path A – Credential Theft (Most Likely)
1. Admin workstation compromised (malware or RAT).
2. Credentials harvested.
3. Attacker logs in from India.
4. DNS and MX records modified.
5. Email and website disrupted.

Likelihood: **High**

---

### Path B – Insider/Former Employee
1. Former employee retained credentials.
2. Logged in from another device.
3. Modified DNS settings as retaliation.

Likelihood: **Medium**

---

### Path C – Password Reuse / Credential Exposure
1. Credentials reused in another breached system.
2. Attacker purchased or found login online.
3. Used immediately to target DNS.

Likelihood: **Medium**

---

## 2. Attack Flow Diagram (ASCII)

```
 Attacker (India)
        |
        |--- Login success (GoDaddy)
        |
   [DNS Control Panel]
        |
        |--- A record modified
        |--- MX record modified
        |
   [Service Outage]
        |
   Emails fail → Website offline
```

---

## 3. Final Hypothesis
The most probable scenario is **credential theft** via RAT or phishing on the administrator’s workstation, followed by a remote login from India, resulting in DNS sabotage.  

