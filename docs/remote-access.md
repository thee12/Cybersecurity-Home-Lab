# Secure Remote Access

## Goal

Provide secure remote management of the lab without exposing Proxmox, SSH, RDP, or the Wazuh dashboard directly to the public internet.

## Tailscale Design

Tailscale is installed on WAZUH01. WAZUH01 acts as a subnet router for the normal management/home subnet:

```text
192.168.1.0/24
```

The isolated attacker subnet is not advertised:

```text
192.168.50.0/24
```

This preserves the isolation of KALI01 while still allowing remote administration of the Proxmox hosts and management services.

## Remote Workflow

```text
Remote device
    |
 Tailscale
    |
 WAZUH01 subnet router
    |
192.168.1.0/24 management network
    |
Proxmox / Wazuh / other lab systems
```

As long as the Proxmox host and WAZUH01 are powered on, a remote Tailscale client can reach the Proxmox web interface using its normal LAN address and start other powered-off VMs as needed.

## Security Notes

- No direct public port forwarding is required.
- The isolated attack subnet is not exported through Tailscale.
- External test users should be removed after validation unless ongoing access is required.
- Tailscale authentication keys and account information must never be committed to this repository.
