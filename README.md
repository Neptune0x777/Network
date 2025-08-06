# Network

***Netstat***
```bash
netstat -rn // will show us the networks accessible
```
***Netcat ncat or nc***
```bash
netcat IP PORT
```
***Nmap***
| Option    | Description                                                     |
|-----------|-----------------------------------------------------------------|
| -sS       | TCP SYN scan (stealth scan)                                     |
| -sT       | TCP connect scan (full connection)                              |
| -sU       | UDP scan                                                        |
| -p        | Specify ports to scan (e.g., -p 80,443,1-100)                   | 
| -p-       | Scan all TCP ports (1 to 65535)                                 |
| -F        | Fast scan: scan only the most popular ports                     |
| -sV       | Service version detection                                       |
| -sC       | Run default scripts (Nmap Scripting Engine - NSE)               |
| -A        | Full scan: OS detection, version detection, scripts, traceroute |
| -T0 to -T5| Set scan speed/aggressiveness (-T0 slowest, -T5 fastest)        |
| -oN       | Save output to normal text file                                  |
| -oX       | Save output to XML format                                       |
| -oG       | Save output in grepable format (for easier parsing)             |
| -n        | No DNS resolution (faster scan)                                 |
| -Pn       | Skip host discovery (treat host as up)                          |
| --script  | Specify NSE scripts to run                                      |
| -sn       | Ping scan: only detect active hosts, no port scan               |

***Ports***

| Port | Protocole | Service         | Description                                                            |
|------|-----------|-----------------|------------------------------------------------------------------------|
| 20/21| TCP	   | FTP             | Uncrypted file transfert                                                |
| 22   | TCP       | SSH             | Secure remote access                                                   |
| 23   | TCP       | Telnet          | Uncrypted remote access                                                |
| 25   | TCP       | SMTP            | Sending emails (unencrypted by default)                                |
| 53   | UDP/TCP   | DNS             | Domain name resolution                                                 |
| 80   | TCP       | HTTP            | Unencrypted web traffic                                                  |
| 161  | TCP/UDP   | SNMP            | Used for network management (v1/v2c are unencrypted)                   |
| 443  | TCP       | HTTPS           | Encrypted web traffic (SSL/TLS)                                          |
| 445  | TCP       | SMB             | File sharing protocol (commonly targeted                               |
| 3389 | TCP       | RDP             | Remote desktop access (often targeted, requires strong authentication) |

