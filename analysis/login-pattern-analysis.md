# Login Pattern Analysis

## Objective
Analyze authentication events across GoDaddy, HostGator, Webflow, and Google to identify anomalies, cross-geo access patterns, and potential credential compromise.

---

## 1. Summary of Observed Events
The following patterns were identified:

- Successful logins from **Mexico** (legitimate admin location).
- Failed and successful logins from **India** (unknown origin).
- Logins from both locations occur within **minutes** of each other.
- DNS changes occur **immediately after** the Indian login.

---

## 2. Correlation Table

| Timestamp | IP | Country | Result | Service |
|----------|------|----------|---------|----------|
| 09:13:21 | 201.180.122.44 | Mexico | SUCCESS | GoDaddy |
| 09:15:49 | 103.221.88.14 | India | FAILED | GoDaddy |
| 09:16:03 | 103.221.88.14 | India | SUCCESS | GoDaddy |
| 09:24:03 | 201.180.122.44 | Mexico | SUCCESS | HostGator |
| 09:28:09 | 103.221.88.14 | India | FAILED | HostGator |

---

## 3. Behavior Assessment

### Legitimate Access Indicators
- The administrator is based in Mexico.
- Most routine activity originates from IP 201.180.122.44.
- Browser and OS: Chrome on Windows (consistent across logs).

### Malicious Access Indicators
- Logins from India occur in intervals too short to represent travel.
- Browser and OS fingerprint differ (Firefox/Linux).
- DNS modifications occur within **2 minutes** of Indian login.
- Failed attempts followed by successful login indicate:
  - Password guessing
  - Credential spraying
  - Reuse of leaked credentials

---

## 4. Technical Conclusion
The login pattern strongly supports **credential compromise**:

- Attacker authenticated successfully after a failed attempt.
- Attacker performed high-impact administrative actions.
- Timing correlation suggests attacker logged in *immediately* after gaining access.

The pattern is **consistent with**:
- Insider threat  
- Stolen credentials  
- Remote Access Trojan (RAT) on admin’s workstation  

---

## 5. Confidence Level
**High confidence**: Authentication compromise  
**Medium confidence**: RAT infection  
**Medium confidence**: Insider involvement  

