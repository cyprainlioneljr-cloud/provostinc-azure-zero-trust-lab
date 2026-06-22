# Provost Inc — Conditional Access Policies

## CA01 — Require MFA for All Staff

### Purpose
Enforce multi-factor authentication for all staff accessing any cloud 
resource, reducing the risk of credential-based compromise.

### Configuration
| Setting | Value |
|---------|-------|
| Included users | Provost-All-Staff group |
| Excluded users | Global Administrator (break-glass account) |
| Target resources | All cloud apps |
| Grant control | Require multifactor authentication |
| Initial state | Report-only |
| Final state | On (enforced) |

### Engineering Approach
1. **Break-glass exclusion:** The Global Administrator account was 
   excluded to prevent tenant lockout — a critical safeguard when 
   deploying any tenant-wide access policy.
2. **Report-only first:** The policy was deployed in Report-only mode 
   to observe its impact via sign-in logs before enforcement.
3. **Validation:** Tested with the SOC Analyst test account (Sarah Chen), 
   which was correctly prompted to register for MFA.
4. **Enforcement:** After validation, the policy was switched to "On".

### Why This Matters
Conditional Access replaces blunt security defaults with granular, 
risk-aware controls — the foundation of a Zero Trust access model.
