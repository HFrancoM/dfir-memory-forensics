# Correlation Matrix – Logs, IOCs and Activity

## Objective
Correlate observed log events with indicators of compromise (IOCs) to support the attack hypothesis and strengthen conclusions about the DNS account compromise.

---

## 1. Data Sources

- `logs/godaddy-access.log`
- `logs/hostgator-admin.log`
- `logs/webflow-access.log`
- `logs/google-activity.json`
- `logs/suspicious-logins.csv`
- `ioc/malicious-ips.txt`
- `ioc/suspicious-domains.txt`
- `ioc/compromised-accounts.txt`
- `ioc/timeline-key-events.txt`

---

## 2. Correlation Matrix

| IOC / Event                         | Source File                      | Correlated Activity                                      | Interpretation                                  |
|-------------------------------------|----------------------------------|---------------------------------------------------------|-------------------------------------------------|
| 103.221.88.14 (India)               | malicious-ips.txt, logs/*       | Failed + successful logins, DNS changes after success   | Strong indicator of compromised access          |
| 201.180.122.44 (Mexico)             | malicious-ips.txt, logs/*       | Routine admin logins, legitimate geography              | Baseline of normal behavior                     |
| A record changed to 185.218.126.92  | godaddy-access.log              | Immediately after Indian login success                   | Unauthorized DNS tampering                      |
| MX changed to malicious.mxserver.cc | godaddy-access.log, hostgator   | Followed by email delivery issues                        | Intentional service disruption                  |
| admin@example.com                   | compromised-accounts.txt        | Target of multiple logins, some from India               | Primary compromised account                     |
| webmaster@example.com               | compromised-accounts.txt        | Webflow login failures                                   | Attempted lateral access                        |
| login from India (Google account)   | google-activity.json            | Precedes DNS change window                               | Indicates broader account exposure              |
| Email failure event                 | hostgator-admin.log             | Occurs after MX record change                            | Confirms impact on messaging infrastructure     |

---

## 3. Key Correlation Findings

1. **Strong temporal correlation** between:
   - Successful login from India  
   - DNS A/MX modification  
   - Email failures  

2. **Multiple systems impacted**:
   - DNS (GoDaddy)
   - Email (HostGator)
   - Web presence (Webflow)
   - Google account

3. **Consistent actor fingerprint**:
   - Same suspicious IP across services
   - Same account targeted repeatedly
   - Same time window

---

## 4. Support to Attack Hypothesis

The correlation matrix supports the hypothesis that:
- An attacker gained valid credentials to the administrator account.
- The attacker logged in from India.
- The attacker intentionally altered DNS and MX records.
- The changes were designed to cause disruption rather than financial gain.

This is consistent with a **sabotage / retaliation** scenario and/or **abuse of compromised credentials**.

