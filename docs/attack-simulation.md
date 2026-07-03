# Provost Inc — Attack Simulation (Atomic Red Team)

## Objective
Safely attack the lab environment on-command to validate detection and 
response coverage, using the Atomic Red Team framework mapped to MITRE ATT&CK.

## Environment
- Target: provost-win-vm (isolated lab VM, resized to B2s for adequate memory)
- Framework: Atomic Red Team (Red Canary)
- Log path: VM -> Azure Monitor Agent -> Log Analytics -> Sentinel

## Techniques Executed
| MITRE ID | Technique | Observed telemetry |
|----------|-----------|-------------------|
| T1087.001 | Account Discovery (local) | whoami.exe, net.exe via Event ID 4688 |
| T1033 | System Owner/User Discovery | whoami.exe |
| T1082 | System Information Discovery | hostname.exe, systeminfo |

## Setup Challenges (real-world troubleshooting)
- **Broken package manager:** PowerShell 5.1 lacked a working NuGet provider; 
  resolved dependency (powershell-yaml) installation issues.
- **Memory constraints:** initial B1s (1 GB RAM) hit OutOfMemoryException; 
  resized VM to B2s (4 GB) to complete installation and testing.
- **Defender quarantine:** Windows Defender flagged Atomic Red Team payloads 
  (by design). Added a scoped Defender exclusion for C:\AtomicRedTeam to permit 
  controlled testing. In production, attack-simulation tooling would run in a 
  segregated environment with compensating controls.

## Safety Measures
- All tests run only on the isolated lab VM
- Cleanup command run after each test to restore known state
- VM deallocated after each session for cost control

## Why This Matters
On-command attack simulation validates that detections actually fire against 
real attacker techniques — the difference between assuming coverage and 
proving it.
