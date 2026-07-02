# Incident Report 001 — Reconnaissance / Discovery Activity

## Summary
During controlled attack simulation (Atomic Red Team) on provost-win-vm, 
reconnaissance activity was executed, detected, investigated, and responded 
to end-to-end. This report documents the full detection-and-response cycle, 
including an identified detection gap and its remediation.

## Classification
- Severity: Medium
- MITRE ATT&CK: T1087 (Account Discovery), T1033 (System Owner/User 
  Discovery), T1082 (System Information Discovery)
- Execution context: T1059.001 (PowerShell)

## Timeline
| Time | Event |
|------|-------|
| T0 | Atomic Red Team discovery techniques executed on provost-win-vm |
| T0 | whoami.exe / hostname.exe spawned by PowerShell (Event ID 4688) |
| T0+min | Telemetry confirmed in Sentinel via SecurityEvent |
| Investigation | Initial detection gap identified (no incident generated) |
| Remediation | New analytics rule authored to close the gap |
| Validation | Re-ran attack; incident created, automation fired, SOC emailed |

## Investigation
Confirmed process-creation telemetry (Event ID 4688). Key finding: discovery 
utilities (whoami, hostname) were spawned BY PowerShell — a strong recon 
signature, since legitimate users rarely invoke these via script in rapid 
succession.

Detection query used:
\```kql
SecurityEvent
| where EventID == 4688
| where NewProcessName has_any ("whoami.exe", "hostname.exe", "net.exe", "nltest.exe")
| where ParentProcessName has_any ("powershell.exe", "cmd.exe")
| project TimeGenerated, Account, Computer, NewProcessName, ParentProcessName
\```

## Detection Gap Identified
The attack generated telemetry but initially produced NO incident — the only 
existing analytics rule targeted failed sign-ins, not process execution. 
Visibility existed, but no detection was watching this behavior.

Contributing finding: initial detection attempts filtered on CommandLine 
content and returned nothing. Investigation revealed Event ID 4688 events 
lacked command-line detail because the "Include command line in process 
creation events" audit policy was not enabled. Detection was adapted to key 
on process name and parent-process relationship instead.

## Remediation
1. Authored analytics rule "Provost - Discovery Tool Execution" (detects 
   discovery utilities spawned by a command shell)
2. Built automation rule "Provost - Notify on Discovery Detection"
3. Wired notification playbook "Provost-Notify-SOC"

## Response Validation (end-to-end)
Re-ran the attack. Confirmed the full chain:
attack -> detection -> incident -> automation rule -> playbook -> SOC email. 
Every stage fired successfully.

## Recommendations
1. Enable command-line process auditing for higher-fidelity detection
2. Add time-based aggregation (multiple discovery tools in a short window = 
   higher confidence, fewer false positives)
3. Extend automated response beyond notification (e.g. host isolation) once 
   detection accuracy is trusted

## Outcome
Completed a full detection-engineering and response cycle: attack -> confirm 
telemetry -> identify gap -> test/refine detection against real data -> deploy 
working detection -> automate response -> validate end-to-end. Detection and 
response coverage measurably improved.
