# Final DFIR Report – DNS Manipulation & Account Compromise

## 1. Executive Summary
The incident involved unauthorized access to administrative accounts controlling DNS and email infrastructure. Attackers modified DNS settings causing website and email disruption for several hours. Available evidence suggests two unauthorized login origins: India and Mexico. Insider involvement is considered possible.

No endpoint forensic acquisition or full log collection was available. This report provides a simulated DFIR reconstruction for portfolio purposes.

## 2. Timeline (Simulated)

| Timestamp | Event |
|----------|-------|
| T0       | Admin reports unusual account activity |
| T1       | DNS records modified in GoDaddy |
| T2       | Website becomes unreachable |
| T3       | HostGator email stops receiving messages |
| T4       | Suspicious login from India observed |
| T5       | Suspicious login from Mexico observed |
| T6       | DNS restored and service resumes |
| T7       | Migration to Google Workspace initiated |

## 3. Key Findings
- Unauthorized login to GoDaddy control panel
- DNS A records modified without authorization
- Email MX records temporarily diverted
- IP origins inconsistent with employee geography
- Administrator workstation likely compromised
- MFA was not enabled for administrative accounts

## 4. Root Cause Analysis
Due to lack of forensic acquisition and limited logs, the precise root cause cannot be confirmed. Evidence strength suggests one of the following vectors:

- Credential theft
- Reuse of old credentials by former employee
- Remote access trojan (RAT) on admin computer

## 5. Recommendations
1. Enforce MFA across all platforms  
2. Conduct credential rotation and remove old accounts  
3. Establish centralized log retention  
4. Implement endpoint hardening  
5. Segregate DNS, website, and email administrative roles  
6. Adopt Google Workspace or Microsoft 365 fully  
7. Conduct security awareness training for staff

## 6. Conclusion
The organization experienced a compromise of administrative access resulting in DNS manipulation and service disruption. Immediate remediation restored normal operations. Additional security controls are required to prevent recurrence.

