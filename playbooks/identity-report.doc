# =====================================================================
# Provost Inc — Identity Reporting Script (read-only)
# Microsoft Graph PowerShell SDK — pulls user & group inventory
# Read-only: creates/changes nothing. Fully commented for learning.
# =====================================================================

# Install the required Graph sub-modules (one-time, current user)
Install-Module Microsoft.Graph.Users -Scope CurrentUser -Force
Install-Module Microsoft.Graph.Groups -Scope CurrentUser -Force

# Connect with READ-ONLY permissions to users and groups
Connect-MgGraph -Scopes "User.Read.All","Group.Read.All"

# Report 1: All users — name, login, and enabled status
# (Confirms lifecycle state, e.g. disabled leavers show AccountEnabled: False)
Get-MgUser -All -Property DisplayName,UserPrincipalName,AccountEnabled |
    Select-Object DisplayName,UserPrincipalName,AccountEnabled |
    Format-Table

# Report 2: All security groups with their object IDs
Get-MgGroup -All | Select-Object DisplayName,Id | Format-Table

# Cleanly end the session
Disconnect-MgGraph
