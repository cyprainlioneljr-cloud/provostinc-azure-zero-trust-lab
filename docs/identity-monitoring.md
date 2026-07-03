# Provost Inc Identity Monitoring & Anomaly Detection

## Objective
Proactively monitor for compromised identities using Entra ID Protection 
(P2) risk signals and User & Entity Behavior Analytics (UEBA).

## Entra ID Protection
- Reviewed the Risk dashboards: Risky users, Risky sign-ins, Risk detections
- Baseline clean (no risk detected)  establishes a "normal" reference point

## Risk-Based Conditional Access (CA02)
The standalone Identity Protection risk policies are being retired 
(October 2026); risk-based access is now implemented through Conditional 
Access. Configured CA02:

| Setting | Value |
|---------|-------|
| Name | CA02 - Sign-in Risk MFA |
| Users | All users (break-glass admin excluded) |
| Condition | Sign-in risk: Medium and High |
| Grant | Require multifactor authentication |
| State | Report-only (validated before enforcement) |

### CA01 vs CA02
- **CA01**  baseline: requires MFA on *every* sign-in (always-on floor)
- **CA02**  adaptive: requires MFA *only* when a sign-in is scored medium/high 
  risk. In production, CA02 would typically escalate further (e.g. require 
  password change or block) rather than duplicate CA01's MFA requirement.

This pairing demonstrates both static and adaptive Zero Trust access control.

## UEBA (User & Entity Behavior Analytics)
- Enabled via System → Settings → Microsoft Sentinel → UEBA tab.
- Data sources: Microsoft Entra ID (sign-in + audit logs).
- Builds dynamic per-entity behavioral baselines over time; anomalies written. 
  to behavior tables for enrichment (not direct alerting).
- Needs days to learn baselines, enabled now so it's ready by end-phase.

## Break-Glass Note
For the lab, the primary admin account serves as the break-glass exclusion. 
In production, a dedicated, cloud-only emergency access account excluded from 
all policies would be used instead, with sign-in alerting on any use.

## Why This Matters
Identity is the primary attack surface in cloud environments. Combining 
risk-based access (Entra ID Protection + Conditional Access) with behavioral 
analytics (UEBA) provides layered detection of compromised identities 
catching both known-bad risk signals and subtle behavioral anomalies.
