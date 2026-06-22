# Provost Inc — Infrastructure Deployment

## Objective
Deploy Provost Inc's first compute resource: a hardened Windows Server VM 
to represent the company's protected internal estate.

## VM Configuration
| Setting | Value |
|---------|-------|
| Name | provost-win-vm |
| OS | Windows Server 2022 Datacenter |
| Size | B1s (burstable, 1 vCPU) |
| Region | East US |
| Resource group | provostinc-soc-lab-rg |
| Auto-shutdown | Enabled (daily) |

## Cost Management
- B1s burstable chosen as the cheapest viable Windows size
- Auto-shutdown enabled at creation to prevent idle running costs
- VM deallocated when not in active use (stopped-deallocated ≈ disk cost only)

## Note: VM Quota Restriction
New pay-as-you-go subscriptions default to zero vCPU quota for many VM 
families. A support request was required to raise the Standard BS Family 
vCPU quota before deployment was possible — a real-world Azure consideration.

## Why This Matters
This VM is the protected counterpart to the future honeypot VM (deployed 
in the live-ops phase). The contrast — a hardened internal host vs. an 
intentionally exposed monitored host — demonstrates defensive posture design.
