# Provost Inc  Access Reviews (Recertification)

## Objective
Periodically recertify that users still require their assigned access, 
supporting least-privilege and audit readiness.

## Review Executed
| Setting | Value |
|---------|-------|
| Name | Provost - Quarterly IT Admin Access Recertification |
| Scope | Provost-IT-Admins group (privileged) |
| Reviewer | Security admin (self-assigned) |
| Recurrence | One time (production: quarterly) |
| Auto-apply results | Enabled (denied users auto-removed) |
| Justification required | Enabled (records rationale for each decision) |
| Decision helpers | Enabled (flags 30 days no sign-in) |

## Outcome
Reviewed membership of Provost-IT-Admins. Each member's access was 
recertified with a documented justification. Decision, reviewer, and 
timestamp captured as audit evidence (see screenshots).

## Why This Matters
Access recertification proves that privileged access is periodically 
validated not merely granted and forgotten. The documented justification 
and auto-apply enforcement are exactly the evidence an ISO 27001 / SOC 2 
auditor requires for access-control assurance.

## Licensing Note
Standard Access Reviews require active Entra ID P2. Executed live during a 
P2 trial window; auto-apply and justification are P2 capabilities. Advanced 
scenarios (ML recommendations, inactive-only reviews, entitlement management) 
require Entra ID Governance.
### Audit evidence

The completed access review shows the recertification decision, reviewer,
justification, and timestamp exactly the evidence an ISO 27001 / SOC 2
auditor requires:

![Access review overview showing completed recertification (progress donut)](../screenshots/Screenshot%202026-07-02%20at%2015.47.40.png)

The privileged group (Provost-IT-Admins) membership was reviewed and
recertified, with auto-apply enforcement and required justification.
