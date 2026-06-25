// ===================================================================
// Provost Inc — Sign-In Hunting Queries
// Source table: SigninLogs (Microsoft Entra ID connector)
// Purpose: identity-attack detection and hunting
// ===================================================================

// 1. All failed sign-ins (ResultType != 0 means "not success")
// Foundation of brute-force / credential-attack detection
SigninLogs
| where ResultType != 0
| project TimeGenerated, UserPrincipalName, ResultType, ResultDescription, IPAddress, Location
| sort by TimeGenerated desc

// 2. Sign-ins grouped by location and IP
// Surfaces geographic anomalies (e.g. logins from unexpected countries)
SigninLogs
| summarize Count = count() by Location, IPAddress
| sort by Count desc

// 3. Brute-force pattern: 5+ failed attempts per user/IP
// This is the logic behind the "Provost - Multiple Failed Sign-Ins" rule
SigninLogs
| where ResultType != 0
| summarize FailedAttempts = count() by UserPrincipalName, IPAddress
| where FailedAttempts >= 5
| sort by FailedAttempts desc

// 4. Risky sign-ins flagged by Entra ID Protection (P2)
// Daily hunt query once live attack data flows in
SigninLogs
| where RiskLevelDuringSignIn in ("medium","high")
| project TimeGenerated, UserPrincipalName, RiskLevelDuringSignIn, IPAddress, Location
