# Insider Risk Evaluation

## Objective
Assess the likelihood that the incident involved an insider or former employee with knowledge of the environment.

---

## 1. Indicators Supporting Insider Involvement

### Access Knowledge
The attacker:
- Knew which systems controlled DNS and email.
- Knew which accounts had administrator rights.
- Executed DNS changes immediately after logging in.

### Motive Indicators
- Administrator workstation had suspected remote access issues.
- A former employee left under hostile circumstances.
- Administrator reported personal harassment.

### Behavioral Flags
- Targeted the domain and email systems specifically.
- Did not attempt financial fraud.
- Attack appears retaliatory, not financially motivated.

---

## 2. Indicators Against Insider Involvement
- Authentication from India may indicate credential exposure online.
- No traceable access from known former employee IP.
- Attacker’s device fingerprint (Firefox/Linux) not consistent with prior employees.

---

## 3. Overall Assessment
| Factor | Weight | Score |
|--------|--------|--------|
| Access knowledge | High | 4/5 |
| Motive | Medium | 3/5 |
| Technical skill | Medium | 3/5 |
| Evidence consistency | Medium | 3/5 |
| Log correlation | Low | 2/5 |

**Total weighted score: 15/25 → 60% Likelihood**

---

## 4. Conclusion
There is a **moderate likelihood (60%)** that insider involvement played a role.  
However, conclusive attribution is not possible without:

- Endpoint memory acquisition  
- Browser artifact review  
- Authentication token analysis  
- Network logs  

