# Provost Inc  IAM Automation (Graph PowerShell)

## Objective
Automate identity reporting via the Microsoft Graph PowerShell SDK, 
demonstrating API-driven identity operations beyond the portal.

## What It Does (read-only)
- Connects to Entra ID with scoped, read-only permissions (least privilege)
- Report 1: all users with enabled/disabled status , validates lifecycle 
  management (Tom Bradley shows AccountEnabled: False, confirming the Sprint 3 
  leaver process)
- Report 2: all security groups with object IDs

## Why Read-Only + Scoped
Requested only User.Read.All and Group.Read.All , least-privilege access. 
The script inspects but never modifies, making it safe to run and audit.

## Why This Matters
Demonstrates automation literacy , the ability to manage identity 
programmatically at scale, not just through the portal. Foundational for 
larger IAM automation (bulk operations, scheduled reports, offboarding 
workflows).

## Production Note
For unattended/scheduled runs, this would use app-only authentication 
(certificate or managed identity) rather than interactive sign-in.
### Report output

Running the read-only Graph report returns the full workforce with account
status. Note **Tom Bradley — AccountEnabled: False**, confirming the Sprint 3
leaver process held, and the `#EXT#` guest from the B2B work:

![Graph PowerShell user and group report showing disabled leaver account](../screenshots/Screenshot%202026-07-02%20at%2019.52.13.png)

This demonstrates API-driven identity operations , inventorying users and
groups programmatically rather than through the portal.
