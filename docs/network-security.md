# Provost Inc Network Security (NSG)

## Objective
Restrict inbound access to provost-win-vm using a Network Security Group, 
reducing the attack surface exposed to the internet.

## Finding & Remediation
| Stage | State |
|-------|-------|
| Initial (insecure) | RDP (3389) open to Any source  exposed to entire internet |
| Hardened | RDP source restricted to administrator's IP only (/32) |

## Steps Taken
1. Identified the default RDP inbound rule allowing source = Any
2. Changed source to a single trusted IP address (administrator's public IP)
3. Verified the rule via the NSG inbound security rules blade

## Why This Matters
Exposing RDP to the internet is a primary attack vector internet-wide 
scanners constantly probe port 3389 for brute-force opportunities. 
Restricting source to a known IP eliminates that exposure for the protected 
VM. (Note: the future honeypot VM will intentionally remain exposed, by 
design, to collect attacker telemetry the opposite philosophy on a 
separate, isolated machine.)
