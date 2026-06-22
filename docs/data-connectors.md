# Provost Inc — Sentinel Data Connectors

## Connectors Configured

### Microsoft Entra ID
| Log type | What it captures |
|----------|-----------------|
| Sign-In Logs | Every authentication, MFA prompt, Conditional Access decision |
| Audit Logs | Directory changes: user lifecycle, PIM activations, group/role changes |
| Non-Interactive Sign-In Logs | Token refreshes, background auth (anomaly detection) |
| User Risk Events / Risky Users | Entra ID Protection risk signals (P2) — feeds Sprint 5 monitoring |

### Azure Activity
- Subscription-scoped, connected via Azure Policy
- Captures all control-plane actions (resource create/modify/delete, RBAC changes)
- Note: policy-based connector has deployment lag (30 min–few hours) before first data

## Verification
Confirmed ingestion via KQL in Advanced Hunting:
- `SigninLogs | take 10` returned live sign-in events ✅
- `AzureActivity` populates after policy deployment completes

## Why This Matters
These connectors turn raw tenant telemetry into queryable security data — 
the foundation for all detection, alerting, and investigation in later sprints.
