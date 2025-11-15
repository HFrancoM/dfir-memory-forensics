# Case Overview – DNS Manipulation & Account Compromise

## Incident Summary
The organization reported unauthorized changes to the DNS configuration of its primary domain, resulting in several hours of website downtime and email disruption. The affected environment included GoDaddy (DNS), HostGator (email hosting), Webflow (website CMS), and Google Drive for file collaboration.

Suspicious logins were identified from IP addresses originating in India and Mexico. Preliminary indicators suggest the involvement of an insider or a former employee with potential access to administrative credentials.

## Business Impact
- Website unavailable for several hours due to DNS manipulation.
- Email delivery failure for engineering and administrative personnel.
- Disruption of DWG file workflow between US and Mexico teams.
- Loss of client communication during the outage window.
- Reputational risk due to external service interruption.

## Environment Summary
- DNS: GoDaddy
- Email: HostGator (prior to migration)
- Website: Webflow
- File storage: Google Drive (non-Workspace)
- OS: Windows endpoints for administrative and engineering users

## Initial Detection
The administrator reported:
- Unexpected account behavior
- Suspicious login notifications
- Loss of DNS and email functionality

## Limitations
- No endpoint forensic acquisition performed
- No full log retention or SIEM
- Only partial logs available through hosting providers
- Root cause not fully confirmed





