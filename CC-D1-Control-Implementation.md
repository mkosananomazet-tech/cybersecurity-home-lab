#ISC2 CC Domain 1: Security Control Implementation
**Date**: 2026-07-01
**Control Implemented**: fail2ban Intrusion Prevention System
**System**: Kali Purple 2025.x | **location**: Johannesburg, SA

## Risk Treatment - Nist RMF Step 4: Implement Controls
| Item | Details |
| --- |--- |
| **Lynis Finding** | DEB-0880: No automated banning of hosts with auth failures |
| **Threat** | Brute-force SSH attacks -> Credential theft -> Confidentiality breach |
| **Vulnerability** | Unlimited authentication attempts allowed on SSH service |
| **Initial Risk** | **High** - SSH exposed without rate-limiting |
| **Control Selected** | **Preventive Technical Control**: fail2ban |
| **Control Function** | Monitors 'var/log/auth.log', bans IP after 5 failures for 10min |
| **CIA Impact** | **Confidentiality**: Protects credentials<br>**Availability: Prevents resource exhaustion |
| **Verification Command** | 'sudo fail2ban-client status sshd' |
| **Verification Result** | Jail active, monitoring '_SYSTEMD_UNIT=ssh.service' |
| **Residual Risk** | **Low** -Distributed/slow attacksmay evade thresholds |

## CC Domain1.3: Security Principles Applied
1. **Defense in Depth**: Layered with ED25519 SSH Keys + UFW Firewall
2. **Least Priviledge**: fail2ban daemon runs as non-root user
3. **Fail Secure**: If fail2ban stops, SSH still requires key auth
 ## Command Evidence
'''bash
$ sudo systemctl status fail2ban
Active: active (running) since Wed 2026-07-01 00:51:25 SAST

$ sudo fail2ban-client status sshd
Status for the jail: sshd
|- Currently banned: 0
`- Total banned: 0
