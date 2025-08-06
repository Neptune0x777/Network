# Network

***Netstat***
```bash
netstat -rn // will show us the networks accessible


| Port | Protocole | Service         | Description                      |
|------|-----------|-----------------|----------------------------------|
| 20/21| TCP	     | FTP             | Uncrypted file transfert        |
| 22   | TCP       | SSH             | Secure remote access           |
| 23   | TCP       | Telnet          | Uncrypted remote access  |
| 25   | TCP       | SMTP            | Sending emails (unencrypted by default)                 |
| 53   | UDP/TCP   | DNS             | Domain name resolution               |
| 80   | TCP       | HTTP            | Unencrypted web traffic                 |
| 161  | TCP/UDP   | SNMP            | Used for network management (v1/v2c are unencrypted) |
| 443  | TCP       | HTTPS           | Encrypted web traffic (SSL/TLS)          |
| 445  | TCP       | SMB             | File sharing protocol (commonly targeted, vulnerable to exploits like EternalBlue) |
| 3389 | TCP       | RDP             | Remote desktop access (often targeted, requires strong authentication) |

