# Investigation Methodology – Account Compromise & DNS Manipulation

## 1. Scoping
- Identify all systems impacted by DNS change
- Review affected hosting providers (GoDaddy, HostGator, Webflow)
- Validate timestamps of the outage
- Determine user accounts with administrative access

## 2. Evidence Collection
(*Simulated for DFIR portfolio purposes*)
- GoDaddy access logs (successful/failed logins)
- HostGator email administration logs
- Webflow account access logs
- Google Drive/Google Account login history
- Collection of suspicious IP addresses
- Timeline entries from system reports and user statements

## 3. Analysis
- Identify login anomalies (geolocations, device fingerprinting)
- Review time correlation between suspicious logins and DNS changes
- Check for password reset events
- Inspect admin panel actions in GoDaddy and HostGator
- Assess potential insider involvement
- Evaluate likelihood of credential theft

## 4. Findings (Simulated)
- Unauthorized DNS modification at timestamp T1
- Administrative panel accessed from IP in India shortly before the change
- Second suspicious login from Mexico within same window
- Administrator workstation exhibited signs of remote access or compromise
- Lack of MFA contributed to unauthorized access

## 5. Containment
- Immediate restoration of DNS settings
- Forced password rotation for all administrative accounts
- Deactivation of unused HostGator accounts
- Migration of corporate email to Google Workspace
- Removal of abandoned infrastructure components

## 6. Recommendations
- Mandatory MFA for all administrative logins
- Full migration away from legacy cPanel hosting
- Audit of DNS and email delegated users
- Endpoint hardening and anti-malware review
- Implementation of least privilege model

