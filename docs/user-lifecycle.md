# Provost Inc — User Lifecycle Management (Joiner / Mover / Leaver)

## Objective
Simulate the full identity lifecycle for a Provost Inc employee, 
demonstrating provisioning, access recalculation, and deprovisioning.

## Test Identity: Tom Bradley

### Joiner (Onboarding)
- Account created with role attributes (Job title: Junior Finance Analyst, 
  Department: Finance)
- Added to groups: Provost-Finance, Provost-All-Staff
- Group-based assignment means access is granted automatically by role

### Mover (Internal Transfer)
- Transferred to Security Operations
- Attributes updated (Job title: SOC Analyst, Department: Security Operations)
- Group membership recalculated: REMOVED from Provost-Finance, ADDED to 
  Provost-SOC
- Removing stale access is the step organizations most often miss, leading 
  to permission accumulation ("access creep")

### Leaver (Offboarding)
- Sign-in blocked (Account enabled = No) — stops all future authentication
- Sessions revoked — invalidates active tokens immediately
- Both actions required: block stops future logins, revoke kills current ones
- Documented final stage: after a retention period, the account would be 
  removed from all groups and deleted (account retained here as evidence)

## Note on Automation
Fully automated joiner/mover/leaver would use Entra ID Governance Lifecycle 
Workflows. That feature requires a separate Entra ID Governance license (not 
included in the E5 trial), so the lifecycle was performed manually here — 
demonstrating the same understanding at zero additional cost. Automated 
Lifecycle Workflows are noted as a future enhancement.

## Why This Matters
Identity lifecycle management is core to identity governance: the right 
access at the right time, and — critically — immediate removal of access 
when it's no longer warranted.
