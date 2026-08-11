# Lessons Learned

## Resource Planning Matters

Running Windows Server, Windows 11, Wazuh, Kali, and a target VM on one host created memory pressure. Splitting the lab across two independent Proxmox hosts made the environment more stable and produced a cleaner separation between defender and attacker infrastructure.

## DNS and Time Are Foundational

Active Directory and security telemetry depend heavily on correct DNS and time synchronization. Several troubleshooting steps reinforced that domain clients should use the domain controller for DNS and that event timelines become difficult to interpret when clocks drift.

## Centralized Configuration Reduces Drift

Wazuh agent groups and centralized `agent.conf` configuration made it easier to apply consistent logging and monitoring settings to workstations and domain controllers.

## Endpoint and Network Visibility Are Different

Wazuh is strong at host-based visibility such as authentication, process, Defender, PowerShell, and FIM events. Basic Nmap activity does not always produce a strong endpoint alert. This demonstrated why a network IDS such as Suricata is complementary rather than redundant.

## Isolation Is a Practical Safety Control

Keeping KALI01 on an isolated `vmbr1` prevented accidental scans or future exploit testing from reaching normal home devices. TARGET01's dual-NIC design allowed telemetry to reach Wazuh while keeping Kali itself off the management network.

## Detection Engineering Requires Validation

A custom Wazuh rule for Registry Run-key persistence did not behave as expected even though built-in FIM rules detected the underlying changes. Rather than assuming the custom rule worked, the lab retained the built-in detection and documented the tuning attempt. This reinforced the importance of validating detections against real generated events.

## Backups Must Be Restored, Not Just Created

A successful backup job is only part of recovery planning. The lab includes a restore-validation step so recovery is demonstrated rather than assumed.
