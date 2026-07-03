# Provost Inc Playbook: Notify SOC

## Objective
Automatically alert the SOC team by email when a security incident is 
created in Microsoft Sentinel.

## Type
Logic Apps Consumption playbook, incident trigger.

## Workflow
| Step | Action |
|------|--------|
| Trigger | Microsoft Sentinel incident created |
| Action | Send an email (Office 365 Outlook) |
| Content | Incident Title, Severity, and Incident URL via dynamic content |

## Design Notes
- Started with a NON-destructive notification playbook (best practice before 
  building any state-changing automation)
- Uses dynamic content so each alert email auto-populates with the specific 
  incident's details.
- Office 365 Outlook connection authorized under the admin account.

## Validation
Manually test-run: succeeded, email delivered. Later validated end-to-end 
via automation rule (see soar-automation.md).

## Why This Matters
Automated notification ensures the SOC is alerted the moment a threat is 
detected reducing response time and removing dependence on someone 
watching a dashboard.
