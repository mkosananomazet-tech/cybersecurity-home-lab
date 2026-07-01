# CC Domain 2: Incident Response - SSH Brute Force Case Study

## 1. Preparation -D2.1
Control Implemented: fail2ban per Lynis DEB-0880. Baseline: SSH on port 22, ED25519 keys only

##2. Detection & Analysis - D2.2
Simulated attack: 5 failed SSH logins from 192.168.1.100
Detection: 'sudo fail2ban-client status sshd' showed ban
Log evidence: '/var/log/auth.log' + 'var/log/fail2ban.log'

##3. Containment - D2.3
Automatic containment: fail2ban added iptables rule DROP for 10min
command: 'sudo iptables -L -n | grep 192.168.1.100'

##4. Eradication & Recovery - D2.4
Threat removed via automatic unban. hardening verified: 'sudo systemctl status fail2ban' active

##5. Lessons Learned -D2.5
Per Sommerville Ch 14.1 'Security Engineering', preventive controls reduce MTTR.
Next: Intergrate with Wazuh SIEM for centralized alerting.

**Frameworks**: NIST 800-61 IR Lifecycle, CC D2.1-D2.5
