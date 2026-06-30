#ISC2 CC Domain 1: Risk Assessment
**Date**: 2026-06-30
**System**: Kali Purple 2025.x | **Location**: Johannesburg, SA
**Assessment Tool**: Lynis 3.x 

## Risk Assessment Table - NIST RMF Step 1: Categorize

| Test ID | Threat | Vulnerability | Risk Level | CC Domain1 Control Type | Mitigation |
| --- | --- | --- |--- |
| **DEB-0880** | Brute-force attack | No automatic IP banning | **high** | **Preventive Technical** | Install 'fail2ban' to auto-block IPs after auth failures |
**BOOT-5122** | Physical tampering | GRUB boot loader has no password | **High** | **Preventive Physical** | Set GRUB password to prevent single-user mode bypass |
| **AUTH-9230** | Password cracking | Weak hashing rounds | **Meium** |**Preventive Technical** | Increase rounds in 'etc/login.defs' to slow brute-force |
| **AUTH9262** | Weak passwords | No strength testing | **Medium** | **Preventive Technical** | Install 'pam_pwquality' for complexity enforcement |
| **AUTH-9282** | Stable accounts | No password expiration | **Medium** | **Detective Administrative** | Set 'PASS MAX DAYS 90' in '/etc/login.defs' |
| **AUTH-9328** | Data exposure | Permissive umask 022 | **Low** | **Preventive Technicals** | Set umask 027 for stricter file permissions |
| **KRNL-5820** | Info disclosure | Core dumps enabled | **Low** | **Preventive Technical** | Disable in '/etc/security/limits.conf' |

##Risk Management Process - CC DOmain 1.5
1. **Identify Asset**: Kali Purple VM used for SOC training
2. **Identify Threat**: External attackers, insider misuse, malware
3. **Identify Vulnerability**: Lynis findings above
4. **Assess Risk**: Likelyhood X impact = Risk Level in table
5. **Treat Risk**: Apply mitigations = **Risk Reduction** strategy

### CIA Triad Mapping
- **Confidentiality Risk**: AUTH-9328 umask -> World-readable files
- **Integrity Risk**: BOOT-5122 GRUB -> Attacker can alter boot process
- **Availability Risk**: DEB-0880 no fail2ban -> DDos via auth spam 
                                                                              
## Control Categories Applied
- **Technical**: fail2ban, pam_pwquality, hashing rounds
- **Administrative**: Password aging policy in '/etc/login.defs'
- **Physical**: GRUB password
                                                                            
### CC Exam Mapping
This lab demonstrates **Domain 1,5: understand Risk Management** and **Domain 1.2: Understand Security Concepts** - specifically control types, CIA Triad,and thee risk equation: 'Risk = Threat x Vulnerability x imppaccct'
