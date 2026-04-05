# Phase 2 — Samba AD Domain Controller

## What was installed
- samba, krb5-config, krb5-user, winbind, libpam-winbind, libnss-winbind

## Domain details
| Property | Value |
|----------|-------|
| Realm | CORP.LOCAL |
| Domain | CORP |
| DC hostname | dc1.corp.local |
| DC private IP | 172.31.42.239 |
| Domain SID | S-1-5-21-616871410-2083744066-560641928 |
| DNS backend | SAMBA_INTERNAL |
| DNS forwarder | 8.8.8.8 |

## Key decisions
- Disabled systemd-resolved (conflict on port 53 with Samba DNS)
- /etc/resolv.conf points to dc1 (172.31.42.239) as primary DNS
- Used --use-rfc2307 for Linux UID/GID support in LDAP

## Verified working
- [x] DNS: corp.local resolves to 172.31.42.239
- [x] Kerberos: kinit administrator@CORP.LOCAL issues ticket
- [x] Domain info: correct forest, domain, DC name
- [x] LDAP: Administrator, Guest, krbtgt visible

## Default AD accounts
| Account | Purpose |
|---------|---------|
| Administrator | Domain admin |
| Guest | Disabled guest account |
| krbtgt | Kerberos ticket signing (never login as this) |

## smb.conf sections explained
- [global] - domain identity and server role
- [sysvol] - replicates Group Policy to all DCs
- [netlogon] - login scripts for domain members
