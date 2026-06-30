# ISC2 CC Domain 1: Security Principles lab
**Date**: 2026-06-30
**Location**: Johannesburg, SA
**System** Kali Purple 2025.x

## Control Implemented: ED25519 SSH Key Authentication

### IAAA Framework
| Component | Implementation |
| --- | --- |
**Identification** | GitHub username: mkosananomazet-tech |
**Authentication** | ED25519 private key challenge-response |
**Authorization** | Key grants 'git push' to owned repos only |
**Accounting** | All commits logged with username + timestamp |

### CIA Triad Impact
1. **Confidentiality**: Private key never leaves Kali. Immune to network sniffing
2. **Integrity**: SHA256:qnBs+5JiDgSaH8PaLuqWx1uUPk++AUurdWzogmuJQ verifies GitHub host
3. **Authentication**: "Something you have" factor - stronger than passwords

### Control Type Analysis
-**Category** Technical Control
- **Function**: Preventive Control - blocks unauthenticated access
- **Risk Mitigated**: Credential theft via phishing. public-key crypto defeats password reuse.

### Threat Modeling
**Threat**: Man-in-the-middle attack during git clone
**Vulnerability**: Trusting DNS/IP without verification + 'known_hosts' file
**Control**: SSH host key fingerprinting verification + 'known_hosts' file
**Residual Risk**: Physical theft of Kali VM -> Mitigated by disk encryption + 'chmod 600' on private key

### CC Domain 1.1 Exam Mapping
This lab demostrates security concepts required for ISC2 CC certification
