# Windows Server RDS Learning Path 64 — Create an RDS Session Host Farm

**Level:** Expert · **Module:** 64/70

## Goal
Operate multiple Session Hosts as one collection with consistent applications, profiles, policies and user experience.

## Setup
1. Verify RDS01 and RDSH02 belong to the same session collection.
2. Standardize OS patch level, GPO, application versions and dependencies.
3. Use shared profile storage.
4. Verify the Broker reconnects users to existing sessions.
5. Test new users across both hosts.
6. Temporarily remove one host from new connections and verify capacity.
7. Create a configuration-drift checklist.

```powershell
Get-RDSessionHost -CollectionName 'RDS-Lab-Desktop' `
 -ConnectionBroker 'RDS01.corp.lab'
Get-RDUserSession -ConnectionBroker 'RDS01.corp.lab'
Get-HotFix -ComputerName RDS01,RDSH02 | Sort-Object PSComputerName,InstalledOn
```

## Evidence
Store host inventory, configuration parity, session distribution, profile consistency, application tests and drift report under `evidence/`.

## Troubleshooting
Uneven user experience usually reflects application, patch, GPO or profile differences. Compare hosts before changing Broker settings.

## Security
All farm members require identical hardening, monitoring and change control.

## Rollback
Drain and remove the nonconforming host until parity is restored.

## Next
`Windows-Server-RDS-Learning-Path-65-Test-RD-Connection-Broker-Load-Balancing`
