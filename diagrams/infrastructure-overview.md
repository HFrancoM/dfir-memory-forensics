# Infrastructure Overview – Affected Environment

## Purpose
Provide a high-level view of the systems, services, and platforms involved in the DNS account compromise incident.

---

## 1. Architecture Diagram (ASCII)

```
                 ┌──────────────────────────┐
                 │       Workstations       │
                 │  Admin PC (Mexico)       │
                 │  Engineering PCs (MX/US) │
                 └───────────┬──────────────┘
                             │
                             ▼
                 ┌──────────────────────────┐
                 │      Cloud Services      │
                 │                          │
                 │  GoDaddy (DNS)           │
                 │  HostGator (Email)       │
                 │  Webflow (Website)       │
                 │  Google Drive / Gmail    │
                 └───────────┬──────────────┘
                             │
                             ▼
                 ┌──────────────────────────┐
                 │       Public Internet     │
                 │   India / Mexico origins  │
                 │   External attackers      │
                 └──────────────────────────┘
```

---

## 2. Platform Roles

### GoDaddy (DNS Provider)
- Controls A/MX/CNAME/TXT records  
- Unauthorized changes detected  
- High-value administrative target  

### HostGator (Legacy Email)
- MX records temporarily pointed away  
- Email queues increased  
- Service disruption visible to customers  

### Webflow (Website CMS)
- Used for public domain landing  
- Authentication attempts from attacker IP  

### Google Drive / Gmail (later Workspace)
- Used for collaboration  
- Login attempts from India  

---

## 3. Administrative Access Flow

1. Admin workstation accessed or compromised  
2. Credentials reused on multiple cloud platforms  
3. Attacker logs in from India  
4. DNS modified → web & email offline  
5. Company migrates to Google Workspace  

