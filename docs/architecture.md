# Architecture

## Overview

This lab uses two independent Proxmox VE hosts to separate the primary IT/security environment from the attacker/test environment while staying within available hardware resources.

## Main Proxmox Host

Roles hosted on the primary node:

- **DC01 / SERVER** — Windows Server 2025 domain controller and DNS server
- **CLIENT01** — Windows 11 Pro domain-joined workstation
- **WAZUH01** — Ubuntu host running the Wazuh manager, indexer, dashboard, and Tailscale subnet router

The main host uses the normal management/home LAN on `192.168.1.0/24`.

## Secondary Proxmox Host

Roles hosted on the secondary laptop:

- **KALI01** — isolated Kali Linux attacker
- **TARGET01** — Ubuntu Server monitored victim/target

The secondary host contains:

- `vmbr0` — management/home LAN
- `vmbr1` — isolated attack network with no physical bridge port and no gateway

## Isolated Attack Network

```text
Network: 192.168.50.0/24
KALI01: 192.168.50.10/24
TARGET01: 192.168.50.20/24
```

KALI01 has only a `vmbr1` interface. TARGET01 has:

1. An attack-side interface on `vmbr1`
2. A management interface on `vmbr0` so it can reach WAZUH01

IPv4 forwarding remains disabled on TARGET01 so it does not become a router between the attack and management networks.

## Design Rationale

The two-host design was selected because the primary host could not comfortably run all VMs at once. Splitting the workload also produced a cleaner security boundary: the primary host represents enterprise/defender infrastructure while the secondary host represents the attack/test environment.

## Remote Administration

WAZUH01 runs Tailscale and advertises only the `192.168.1.0/24` management subnet. Remote clients can therefore reach Proxmox and management services without exposing them directly to the public internet.

The `192.168.50.0/24` attack subnet is intentionally not advertised.
