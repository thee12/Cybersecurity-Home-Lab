# Screenshot Guide

Add sanitized screenshots that prove the major parts of the lab without exposing secrets or personal information.

Recommended screenshots:

1. Proxmox VM inventory on the main host
2. Proxmox VM inventory on the secondary host
3. Active Directory OU structure
4. Group Policy configuration
5. Wazuh agent inventory
6. Custom SOC dashboard
7. Failed SSH authentication alert from TARGET01
8. Windows or Linux FIM alert
9. Defender/EICAR alert
10. Kali Nmap output against TARGET01
11. Successful Proxmox backup task
12. Successful restore validation
13. Tailscale subnet-route configuration with sensitive account details cropped

## Before Uploading

Remove or crop:

- Passwords
- API/authentication keys
- Tailscale auth keys
- Personal email addresses
- Public IP addresses if present
- Browser tabs containing unrelated private information
- Any credentials or tokens shown in terminals
