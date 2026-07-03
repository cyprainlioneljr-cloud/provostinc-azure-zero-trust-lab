# Provost Inc   Role-Based Access Control (RBAC)

## Objective
Implement least-privilege access using both built-in and custom Azure RBAC 
roles, mapped to Provost Inc job functions.

## Built-in Role Assignment
| Role | Assigned to | Scope | Purpose |
|------|-------------|-------|---------|
| Reader | Provost-SOC group | Resource group | SOC can view all resources but not modify |

## Custom Role: Provost-SOC-VM-Operator
**Scenario:** SOC analysts need to start/restart VMs during incident 
response, but must NOT be able to delete VMs or change networking. No 
built-in role fit this exactly  so a custom role was authored.

Permissions granted (control-plane Actions):
- Microsoft.Compute/virtualMachines/read
- Microsoft.Compute/virtualMachines/start/action
- Microsoft.Compute/virtualMachines/restart/action
- Microsoft.Compute/virtualMachines/instanceView/read

Deliberately excluded: no delete, no write (reconfigure), no network 
permissions. This is least privilege  exactly the operations needed, 
nothing more.

## Key Lesson: Global Admin ≠ Subscription Owner
A critical early discovery: the native admin@ account held **Global 
Administrator** (an Entra ID / directory role) but could not create or 
manage Azure resources it had no **Azure RBAC** role on the subscription.

Entra directory roles and Azure RBAC roles are completely separate systems:
- **Entra ID roles** (e.g. Global Administrator) : govern identity and 
  directory objects (users, groups, Conditional Access)
- **Azure RBAC roles** (e.g. Owner, Contributor) : govern Azure *resources* 
  (subscriptions, resource groups, VMs)

The fix: assign the admin@ account **Owner** on the subscription. Notably, 
Owner and Contributor are classified by Azure as **Privileged Administrator 
Roles**  separated in the portal from "Job function roles" because they 
can delegate access to others. This is an intentional governance guardrail.

## Why This Matters
Understanding the boundary between directory roles and resource RBAC is 
fundamental to Azure access governance, and a common real-world stumbling 
block. Custom roles demonstrate the ability to design precise least-privilege 
access where built-in roles don't fit.
