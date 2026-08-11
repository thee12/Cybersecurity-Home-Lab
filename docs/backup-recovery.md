# Backup and Recovery

## Objective

Validate that important lab VMs can be recovered after a failed configuration change, corruption, or other lab mistake.

## Recommended Backup Scope

Create Proxmox backups for at least:

- DC01 / SERVER
- CLIENT01
- WAZUH01
- TARGET01 after monitoring configuration is stable

## Backup Procedure

For each VM:

1. Open the VM in Proxmox.
2. Select **Backup**.
3. Choose the configured backup storage.
4. Use snapshot mode when supported.
5. Start the backup and confirm the job completes successfully.

## Restore Validation

A backup is not fully validated until a restore has been tested.

Recommended process:

1. Select a non-critical VM such as CLIENT01.
2. Restore the backup using a new VM ID when possible rather than overwriting the working VM.
3. Boot the restored VM.
4. Verify basic OS functionality.
5. Verify network connectivity.
6. Verify domain/Wazuh connectivity if applicable.
7. Delete the temporary restored VM after validation.

## Evidence to Capture

Add screenshots showing:

- Successful Proxmox backup task
- Backup file listed in storage
- Restored VM booted successfully
- Optional domain/Wazuh connectivity after restore

## Status

This document is intentionally a validation checklist. Update it with the exact backup storage, dates, and restore-test results after the final recovery test is completed.
