# Provost Inc User Accounts

This document records the workforce identities created in Microsoft Entra ID 
for the Provost Inc SOC lab.

| Display Name | Username (UPN) | Role in Organization |
|-------------|----------------|---------------------|
| James Okafor | j.okafor | Finance Analyst |
| Sarah Chen | s.chen | SOC Analyst (test user) |
| Michael Adeyemi | m.adeyemi | IT Administrator |
| Lisa Romano | l.romano | HR Manager |
| David Park | d.park | Executive (high-value target) |

## Design Notes
- All accounts created under the tenant domain (onmicrosoft.com).
- Passwords are auto-generated and stored securely outside this repo.
- Sarah Chen is used as the standard test account for validating 
  Conditional Access policies.
- David Park represents a high-value executive target useful for 
  later attack-simulation and risk-based access scenarios.
