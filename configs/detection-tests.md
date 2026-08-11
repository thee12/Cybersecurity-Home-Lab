# Detection Test Matrix

| Test | Source | Target | Telemetry / Detection | Status |
|---|---|---|---|---|
| Failed Windows authentication | CLIENT01 / domain | DC01 | Windows Security / Wazuh | Validated |
| PowerShell activity | CLIENT01 / DC01 | Local endpoint | Event ID 4104 / Wazuh | Validated |
| Sysmon process activity | CLIENT01 / DC01 | Local endpoint | Sysmon Operational / Wazuh | Validated |
| Defender EICAR test | CLIENT01 | Windows Defender | Defender Operational / Wazuh | Validated |
| Windows file change | CLIENT01 | `C:\LabMonitored` | Wazuh FIM | Validated |
| Registry Run-key modification | CLIENT01 | HKLM Run key | Wazuh Registry FIM | Validated |
| Nmap service scan | KALI01 | TARGET01 | Service exposure/reconnaissance | Validated |
| Failed SSH logins | KALI01 | TARGET01 | Linux authentication / Wazuh | Validated |
| Successful SSH login | KALI01 | TARGET01 | Linux authentication / Wazuh | Validated |
| Linux test-directory change | TARGET01 | `/LabMonitored` | Wazuh FIM | Validated |
| Temporary Linux user creation | TARGET01 | Account files | Wazuh FIM | Validated |
| Proxmox backup + restore | Proxmox | Selected VM | Recovery validation | Pending final restore proof |
| Suricata network IDS | Future | Attack segment | Network-based detection | Deferred |

## Notes

The purpose of this matrix is to connect an action to the telemetry source and observable result. It should be updated when new detections or network sensors are added.
