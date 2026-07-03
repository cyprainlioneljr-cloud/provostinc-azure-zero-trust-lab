# Provost Inc Analytics Rule: Multiple Failed Sign-Ins

## Rule Name
Provost Multiple Failed Sign-Ins

## Objective
Detect accounts experiencing 5 or more failed sign-in attempts in a short 
window a signature of brute-force or password-spray attacks.

## Detection Logic (KQL)
kql
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count() by UserPrincipalName, IPAddress
| where FailedAttempts >= 5


## Configuration
| Setting | Value |
|---------|-------|
| Type | Scheduled query rule |
| Severity | Medium |
| MITRE ATT&CK | Credential Access (T1110 - Brute Force) |
| Run frequency | Every 1 hour |
| Lookback period | 1 hour |
| Alert threshold | Results > 0 |
| Status | Enabled |

## Entity Mapping
| Entity | Mapped field |
|--------|-------------|
| Account | UserPrincipalName |
| IP | IPAddress |

Entity mapping makes generated incidents investigable analysts can pivot 
directly on the affected account and source IP.

## Why Threshold = 5
Five failures balances detection sensitivity against false positives. A 
genuine user mistyping a password rarely fails 5+ times in an hour; an 
automated attack easily does. The threshold can be tuned as real data 
accumulates.

## Note on Defender Portal Incident Handling
Because Sentinel is onboarded to the Defender portal, the Defender XDR 
correlation engine governs incident creation and naming. Alerts from this 
rule surface in the unified Defender incident queue.

## Current State / Honeypot Readiness
With only legitimate lab users present, this rule rarely fires today by 
design. It is armed and ready: when the end-phase honeypot attracts real 
brute-force traffic, this rule will generate live incidents with no rework.
