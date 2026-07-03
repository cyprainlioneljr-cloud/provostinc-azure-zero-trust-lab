# Provost Inc Privileged Identity Management (PIM)

## Objective
Eliminate standing administrative access by making privileged roles 
**eligible** rather than permanently active, enforcing just-in-time (JIT) 
elevation.

## Configuration
| Setting | Value |
|---------|-------|
| Role managed | User Administrator |
| Assigned to | Michael Adeyemi (IT Admin) |
| Assignment type | Eligible (not Active) |
| Activation requirement | MFA + justification |

## How It Works
- Michael does **not** hold User Administrator rights permanently.
- When he needs the role, he activates it via PIM for a limited duration.
- Activation requires MFA and a written justification, and is fully logged.

## Why This Matters
Standing admin accounts are a primary target for attackers. JIT access 
through PIM means there is no permanent privileged account to compromise, 
dramatically reducing the attack surface a core Zero Trust control.
