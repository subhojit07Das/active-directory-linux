 Phase 3 — Users, Groups and Organizational Units

## Organizational Units created
| OU | Purpose |
|----|---------|
| OU=IT | IT department |
| OU=HR | HR department |
| OU=Finance | Finance department |

## Security groups
| Group | OU | Purpose |
|-------|----|---------|
| G_IT | OU=IT | IT staff - access to IT share |
| G_HR | OU=HR | HR staff - access to HR share |
| G_Finance | OU=Finance | Finance staff - access to Finance share |

## Users created
| Username | Group | UPN |
|----------|-------|-----|
| alice | G_IT | alice@corp.local |
| carol | G_HR | carol@corp.local |
| eve | G_Finance | eve@corp.local |

## Key LDAP concepts learned
- distinguishedName: unique path to every object in LDAP tree
- objectSid: unique security identifier, used for all permissions
- userAccountControl: single integer controlling account state (512=enabled)
- memberOf: group memberships, checked at login for permissions
- userPrincipalName: modern login format (alice@corp.local)

## Commands reference
- samba-tool ou create: create organizational unit
- samba-tool group add: create security group
- samba-tool user create: create domain user
- samba-tool group addmembers: add user to group
- samba-tool user show: view full LDAP record of a user
