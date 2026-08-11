# Attack Lab

## Purpose

The attack portion of the lab validates that endpoint and authentication telemetry can be generated in a controlled environment and investigated in Wazuh.

All tests are limited to systems owned and configured for this home lab.

## Network Layout

```text
KALI01 192.168.50.10/24
        |
      vmbr1
        |
TARGET01 192.168.50.20/24
```

KALI01 is isolated from the normal home LAN. TARGET01 has a second management interface so it can communicate with WAZUH01 without routing Kali traffic into the management network.

## Tests Performed

### Nmap Reconnaissance

Example:

```bash
nmap -sV 192.168.50.20
```

This validated host reachability, exposed services, and the difference between open and closed ports.

### SSH Authentication Testing

Controlled failed SSH logins were generated from KALI01 and observed in TARGET01 authentication logs and Wazuh.

A successful SSH login was also performed for comparison with failed authentication events.

### File Integrity Testing

A dedicated directory was monitored:

```text
/LabMonitored
```

Files were created, modified, and deleted to validate Linux FIM telemetry.

### Account-File Testing

A temporary Linux user was created and removed, causing changes to account-related files such as `/etc/passwd`, `/etc/group`, and `/etc/shadow`.

Wazuh FIM events were reviewed to confirm the changes were detected.

## Observations

Wazuh provided strong visibility into endpoint and authentication events. Basic Nmap reconnaissance itself may not generate a strong host-based alert unless the scan causes a logged endpoint event. A network IDS such as Suricata is a future extension for direct network-traffic detection.
