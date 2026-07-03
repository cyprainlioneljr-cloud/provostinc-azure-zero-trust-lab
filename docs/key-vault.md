# Provost Inc  Azure Key Vault

## Objective
Deploy a Key Vault to securely store secrets, keys, and certificates, 
using the modern Azure RBAC permission model.

## Configuration
| Setting | Value |
|---------|-------|
| Name | provost-kv-cff |
| Tier | Standard |
| Permission model | Azure RBAC (not legacy access policies) |
| Test secret | ProvostTestSecret |

## Key Lesson: Management Plane vs Data Plane
Creating the Key Vault did NOT grant permission to read or write its 
secrets attempting to view secrets returned "The operation is not 
allowed by RBAC."

This is by design. Azure separates two layers of access:
- **Management plane** (Owner, Contributor) : manage the vault *resource* 
  itself (create, delete, configure)
- **Data plane** (Key Vault Secrets Officer, Secrets User) : work with the 
  vault's *contents* (the actual secrets, keys, certificates)

Even as subscription Owner, data-plane access had to be explicitly granted 
by assigning the **Key Vault Secrets Officer** role on the vault. Only then 
could secrets be created and read.

## Why This Matters
This separation enforces least privilege: someone who can manage the vault 
resource cannot automatically read its sensitive contents. It mirrors the 
broader lesson that different Azure access systems are deliberately 
independent (see rbac.md "Global Admin ≠ subscription Owner").
