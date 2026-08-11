# Diagram Guide

Create a network/architecture diagram showing the following components:

- Home router / management LAN (`192.168.1.0/24`)
- Main Proxmox host
  - DC01 / SERVER
  - CLIENT01
  - WAZUH01
- Secondary Proxmox host
  - TARGET01
  - KALI01
- `vmbr0` management connectivity
- `vmbr1` isolated attack network (`192.168.50.0/24`)
- KALI01 connected only to `vmbr1`
- TARGET01 dual-NIC design
- WAZUH01 as the Tailscale subnet router
- Remote Tailscale client reaching the management subnet

The diagram should emphasize that the attack subnet is isolated and is not advertised through Tailscale.
