# Provost Inc Microsoft Sentinel Deployment

## Objective
Deploy a SIEM for Provost Inc using Microsoft Sentinel on a dedicated 
Log Analytics workspace, managed through the Microsoft Defender portal.

## Architecture Decisions
| Decision | Choice | Rationale |
|----------|--------|-----------|
| Workspace | `provost-soc-laws` (dedicated, clean) | Sentinel cannot be installed on Defender-for-Cloud default workspaces |
| Region | East US | Consistent with project resources |
| Retention | 90 days | Default 30 days limits Sentinel features; 90 days also supports future honeypot data |
| Management portal | Microsoft Defender portal (security.microsoft.com) | 2026 standard; Azure portal Sentinel experience retires March 2027 |

## Licensing / Cost
- Sentinel free trial active (10 GB/day free ingestion, through ~22 Jul 2026)
- Lab-scale identity/activity logs are well under the free grant
- After trial: pay-per-GB, but lab volumes remain a few dollars/month

## Honeypot Readiness
Workspace built clean with 90-day retention so the end-phase honeypot 
attack data flows into the existing SIEM with no rework only one 
additional connector required when the honeypot goes live.
