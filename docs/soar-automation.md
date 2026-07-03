# Provost Inc SOAR Automation Pipeline

## Objective
Connect detection to automated response, so that a detected threat 
automatically triggers a notification — the core of SOAR (Security 
Orchestration, Automation, and Response).

## The Full Chain

Attack executed (Atomic Red Team)
  -> SecurityEvent logged to Sentinel
  -> Analytics rule detects it (Provost - Discovery Tool Execution)
  -> Incident created
  -> Automation rule triggers (Provost - Notify on Discovery Detection)
  -> Playbook runs (Provost-Notify-SOC)
  -> SOC receives email alert


## Components
| Component | Name | Role |
|-----------|------|------|
| Detection | Provost - Discovery Tool Execution | Analytics rule that creates the incident |
| Automation rule | Provost - Notify on Discovery Detection | Triggers on incident creation, condition-scoped to the discovery rule |
| Playbook | Provost-Notify-SOC | Sends the SOC email |

## Key Configuration Notes
- **Standard vs Enhanced automation rules:** In the current Defender portal, 
  incident-triggered automation lives under "Standard rules" (single-workspace), 
  while "Enhanced rules" are alert-triggered and tenant-wide. Standard rules 
  were used here for incident-based response in a single workspace.
- **Analytics rules can no longer call playbooks directly** (deprecated 2023); 
  the modern pattern is analytics rule -> automation rule -> playbook.

## Key Lesson: Sentinel Service Account Permissions
The automation rule initially failed to save. Cause: Microsoft Sentinel's 
service account ("Azure Security Insights") lacked permission to run the 
playbook. Even as subscription Owner, this separate service identity needed 
explicit rights.

Fix: assigned the **Microsoft Sentinel Automation Contributor** role to the 
Azure Security Insights service account on the resource group containing the 
playbook. After propagation, the automation rule saved and ran successfully.

This mirrors a recurring lesson in this project: separate identities require 
separate, explicit grants (Global Admin != subscription Owner; management 
plane != data plane; and here, the Sentinel service account != the user).

## Validation
End-to-end test confirmed: attack -> incident created -> automation rule 
fired -> playbook ran -> email delivered. Full chain operational.

## Why This Matters
This is what turns a SIEM into a SOAR platform — detections don't just sit 
in a queue, they trigger consistent, automated response with no analyst delay.
### Automation rule wiring

The automation rule triggers on incident creation, scoped by condition to the
discovery detection, and runs the notification playbook:

![Automation rule condition and Run playbook action](../screenshots/Screenshot%202026-07-02%20at%2014.35.59.png)

This connect detection to automated response: incident created →
automation rule fires → Provost-Notify-SOC playbook runs → SOC alerted.
### Detection signature

Discovery utilities (`whoami.exe`, `hostname.exe`) were observed spawning
**from PowerShell** — a strong reconnaissance indicator, since legitimate
users rarely invoke these via script in rapid succession:

![whoami.exe and hostname.exe spawned by PowerShell in SecurityEvent data](../screenshots/Screenshot%202026-07-02%20at%2014.34.02.png)

This process-name + parent-process pattern became the basis for the
"Provost Discovery Tool Execution" analytics rule.
