# Active Directory

## Domain

The lab Active Directory domain is:

```text
ad.home.arpa
```

The Windows Server VM acts as the domain controller and DNS server.

## Implemented Components

- Active Directory Domain Services
- DNS
- Organizational Units for users, workstations, servers, groups, and service accounts
- Separate standard-user and administrative accounts
- Windows 11 Pro domain join
- Group Policy baselines for workstations and domain controllers

## Group Policy and Auditing

Security-focused policies include:

- PowerShell Script Block Logging
- Process Creation auditing
- Command-line inclusion in process creation events
- Workstation security baseline
- Domain controller security baseline

These policies provide higher-quality endpoint telemetry for Wazuh and improve visibility during controlled testing.

## Validation

Validation included:

- Confirming CLIENT01 joined the domain
- Confirming DNS resolution for the domain/controller
- Applying Group Policy and checking effective policy
- Generating PowerShell and process events for Wazuh ingestion
- Testing failed authentication and account-related security events
