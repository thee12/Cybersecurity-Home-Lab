# Wazuh Monitoring

## Overview

WAZUH01 runs an all-in-one Wazuh deployment and provides centralized visibility for Windows and Linux endpoints in the lab.

## Monitored Endpoints

- **CLIENT01** — Windows 11 workstation
- **SERVER / DC01** — Windows Server domain controller
- **TARGET01** — Ubuntu Server attack target

## Windows Telemetry

Collected Windows sources include:

- Windows Security Event Log
- Sysmon Operational log
- Microsoft Defender Operational log
- PowerShell Operational log
- File Integrity Monitoring
- Registry Integrity Monitoring

## Agent Organization

Windows agents are organized by role using centralized Wazuh agent groups and labels.

Examples:

```text
windows-workstations -> CLIENT01
domain-controllers   -> SERVER / DC01
```

Role labels were also used to distinguish workstation and domain-controller telemetry.

## File Integrity Monitoring

Windows FIM was used for:

- A dedicated monitored test directory
- Registry Run and RunOnce keys

Linux FIM on TARGET01 was used for:

- `/LabMonitored`
- `/etc/passwd`
- `/etc/group`
- `/etc/ssh`
- Account-related system files modified during temporary-user tests

## Detection Validation

The lab generated and reviewed events for:

- Failed logins and account lockouts
- PowerShell activity
- Sysmon process events
- Microsoft Defender/EICAR detections
- File additions, modifications, and deletions
- Registry Run-key changes
- Linux SSH authentication activity
- Linux account-file changes

## Dashboarding

A custom SOC dashboard was created with views such as:

- Alerts by severity
- Alerts by endpoint
- Top alert types
- Alerts over time
- High-severity alert count

Saved searches/filters were also created for common investigative workflows.

## Custom Rule Experimentation

A custom registry-persistence rule was tested for Windows Run-key changes. Built-in Wazuh FIM rules successfully detected the changes, while the custom rule required additional tuning. The exercise was retained as a detection-engineering lesson rather than blocking completion of the broader lab.
