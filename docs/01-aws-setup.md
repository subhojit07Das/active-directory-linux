# Phase 1 — AWS Setup

## Instances
| Host | Private IP | Role |
|------|------------|------|
| dc1.corp.local | 172.31.42.239 | Samba AD Domain Controller |
| fs1.corp.local | 172.31.39.134 | Samba File Server |
| client1.corp.local | 172.31.42.3 | Domain-joined Linux client |

## Domain name
`corp.local`

## Security group: ad-lab-sg
| Port | Protocol | Source | Purpose |
|------|----------|--------|---------|
| 22 | TCP | My IP/32 | SSH |
| 445 | TCP | 172.31.0.0/16 | SMB |
| 636 | TCP | 172.31.0.0/16 | LDAPS |
| 389 | TCP | 172.31.0.0/16 | LDAP |
| 135 | TCP | 172.31.0.0/16 | RPC |
| ICMP | All | 172.31.0.0/16 | Ping |
| 53 | TCP+UDP | 172.31.0.0/16 | DNS |
| 88 | TCP+UDP | 172.31.0.0/16 | Kerberos |

## Networking
- All 3 instances in same VPC: vpc-0e405089cf3640c9e
- /etc/hosts configured on all 3 machines as temporary DNS
- Permanent DNS will come from Samba DC after Phase 2
- Ping verified between all 3 machines by hostname and IP
