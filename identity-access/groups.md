# Provost Inc Security Groups

Security groups segment access by role, supporting least-privilege and 
Zero Trust principles.

| Group Name | Members | Purpose |
|-----------|---------|---------|
| Provost-Finance | James Okafor | Finance resource access |
| Provost-SOC | Sarah Chen | Security operations access |
| Provost-IT-Admins | Michael Adeyemi | Administrative functions |
| Provost-HR | Lisa Romano | HR resource access |
| Provost-Executives | David Park | Executive access (elevated monitoring) |
| Provost-All-Staff | All users | Org-wide policy targeting (e.g. MFA) |

## Design Notes
- All groups are **Security** type with **Assigned** membership.
- Provost-All-Staff is used to apply organization-wide controls such 
  as the MFA Conditional Access policy.
- Group-based assignment means new users inherit policy automatically 
  when added to the right group.
