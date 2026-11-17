# Active Directory & Windows Security Lab

**Project 3 | Windows Server 2022 | Active Directory | Windows Security**

## 1. Project Overview

Built a Windows domain environment using VMware Workstation, Windows Server 2022, and a Windows 11 workstation.

The project focused on Active Directory deployment, DNS configuration, domain joining, Group Policy, security auditing, Windows Firewall, and endpoint hardening.

## 2. Lab Environment

| Component | Configuration |
|---|---|
| Domain Controller | Windows Server 2022 (DC01) |
| Client | Windows 11 (CLIENT01) |
| Domain | lab.local |
| Domain Controller IP | 192.168.136.131 |
| Network | VMware NAT |
| Virtualization | VMware Workstation |

## 3. Active Directory Configuration

- Installed Active Directory Domain Services.
- Created the `lab.local` domain.
- Created Organizational Units: Admins, Workstations, Servers, Security Groups.
- Moved CLIENT01 into the Workstations OU.
- Created domain user: `doon.admin`.
- Created groups: Employees and IT-Admins.

## 4. DNS & Domain Join

Configured CLIENT01 to use DC01 as its DNS server.

Tested DNS resolution:

```cmd
nslookup lab.local
```

Domain resolution: `192.168.136.131`

Successfully joined CLIENT01 to the `lab.local` domain.

## 5. Group Policy

Created a GPO named **Workstation Security Baseline** and linked it to the Workstations OU.

Configured:
- Password policies
- Account lockout policies
- Security auditing
- Workstation security settings

Verified applied policies using:

```cmd
gpresult /scope computer /r
```

Confirmed:
- Workstation Security Baseline
- Default Domain Policy

## 6. Security Auditing & Windows Firewall

**Advanced Security Auditing**

Configured:
- Credential Validation
- Kerberos Authentication Service
- Logon
- Logoff
- Account Lockout
- User Account Management
- Security Group Management
- Audit Policy Change

Verified using:

```cmd
auditpol /get /category:*
```

Reviewed Windows Security logs through Event Viewer.

Event ID **4634** was recorded for `LAB\doon.admin`.

**Windows Defender Firewall**

- Domain Profile enabled on CLIENT01.
- Inbound connections blocked by default.
- Outbound connections allowed by default.
- Firewall settings controlled through Group Policy.

## 7. Endpoint Hardening & Troubleshooting

**Endpoint Hardening**
- Disabled the local Guest account on CLIENT01.

**Troubleshooting**

The initial domain join failed because the credentials entered were incorrect. After correcting the credentials, CLIENT01 successfully joined `lab.local`.

## 8. Results & Evidence

The lab was completed successfully.

- CLIENT01 joined to the `lab.local` domain.
- CLIENT01 placed in the Workstations OU.
- Workstation Security Baseline GPO applied.
- Security audit events generated.
- Windows Defender Firewall configured.
- Local Guest account disabled.

### Technical Evidence Report

The report contains screenshots from the actual lab documenting Active Directory, DNS, Group Policy, security auditing, Windows Firewall, and endpoint configuration.

📄 **[View Project 3 — Active Directory Evidence Report](PROJECT3_AD_SECURITY_EVIDENCE_REPORT_2026.pdf)**

---

*Windows domain administration and security configuration using VMware Workstation.*
