# Network

***Netstat***
```bash
netstat -rn // will show us the networks accessible
```
***Netcat ncat or nc***
```bash
nc IP PORT
```
| Option       | Description                                                            |
|--------------|------------------------------------------------------------------------|
| `-l`         | Listen mode (waits for incoming connection)                            |
| `-v`         | Verbose mode (prints connection details)                               |
| `-n`         | Do not resolve DNS (use raw IP addresses)                              |
| `-p <port>`  | Specify source port (used with `-l`)                                   |
| `-e <cmd>`   | Execute a command after connection (⚠️ often disabled for security)    |
| `-c <cmd>`   | Same as `-e`, but uses internal shell (less common)                    |
| `-u`         | Use UDP instead of TCP                                                 |
| `-z`         | Zero-I/O mode (used for port scanning)                                 |
| `-w <sec>`   | Set connection timeout in seconds                                      |
| `-k`         | Keep listening after a connection closes (server mode)                 |
***FTP***
```bash
ftp -p <TARGET> // -p passive mode
```
| Command       | Description                                       |
|---------------|---------------------------------------------------|
| `ls`          | List files in the current remote directory         |
| `cd <dir>`    | Change directory on the remote server             |
| `pwd`         | Show the current remote working directory         |
| `get <file>`   | Download a file from the server to your machine    |
| `put <file>`   | Upload a file from your machine to the server      |
| `mget <files>` | Download multiple files (wildcards allowed)        |
| `mput <files>` | Upload multiple files                              |
| `delete <file>`| Delete a file on the remote server                 |
| `mkdir <dir>` | Create a directory on the remote server           |
| `rmdir <dir>` | Remove a directory on the remote server           |
| `binary`      | Switch to binary transfer mode (for non-text files)|
| `ascii`       | Switch to ASCII transfer mode (for text files)     |
| `passive`     | Toggle passive mode on/off                         |
| `help`        | Show available FTP commands                       |
| `bye` / `exit`| Disconnect and close the FTP session              |
***Nmap***
```bash
nmap -OPTIONS IP
```
| Option    | Description                                                       |
|-----------|-------------------------------------------------------------------|
| `-sS`       | TCP SYN scan (stealth scan)                                     |
| `-sT`       | TCP connect scan (full connection)                              |
| `-sU`       | UDP scan                                                        |
| `-p`        | Specify ports to scan (e.g., -p 80,443,1-100)                   | 
| `-p-`       | Scan all TCP ports (1 to 65535)                                 |
| `-F`        | Fast scan: scan only the most popular ports                     |
| `-sV`       | Service version detection                                       |
| `-sC`       | Run default scripts (Nmap Scripting Engine - NSE)               |
| `-A`        | Full scan: OS detection, version detection, scripts, traceroute |
| `-T0 to -T5`| Set scan speed/aggressiveness (-T0 slowest, -T5 fastest)        |
| `-oN`       | Save output to normal text file                                  |
| `-oX`       | Save output to XML format                                       |
| `-oG`       | Save output in grepable format (for easier parsing)             |
| `-n`        | No DNS resolution (faster scan)                                 |
| `-Pn`       | Skip host discovery (treat host as up)                          |
| `--script`  | Specify NSE scripts to run                                      |
| `-sn`       | Ping scan: only detect active hosts, no port scan               |

| Script Category      | Example Script        | Description                                                                 |
|----------------------|-----------------------|-----------------------------------------------------------------------------|
| default              | -                     | Default script set (used with `-sC`)                                        |
| safe                 | -                     | Scripts considered non-intrusive                                            |
| vuln                 | `vulners`, `http-vuln*`| Checks for known vulnerabilities (CVEs, exploits)                          |
| auth                 | `ftp-anon`, `http-auth`| Authentication-related checks (e.g., anonymous login)                      |
| brute                | `ssh-brute`, `ftp-brute`| Performs brute force attacks on various protocols                         |
| discovery            | `broadcast-dhcp-discover`, `dns-brute` | Gathers information from the network                       |
| dos                  | `http-slowloris`      | Denial of service testing (⚠️ dangerous)                                    |
| exploit              | `http-shellshock`, `ftp-proftpd-backdoor` | Attempts known exploits (⚠️ dangerous)                  |
| malware              | `http-malware-host`, `irc-unrealircd-backdoor` | Detects backdoors or malware-infected services     |
| safe version scan    | `banner`, `http-title`| Basic fingerprinting/info gathering                                          |
| smb                  | `smb-enum-shares`, `smb-os-discovery` | SMB-related information and vulnerability checks            |
| ssl                  | `ssl-cert`, `ssl-enum-ciphers` | Checks for SSL/TLS certificate info and weak ciphers                |
| http                 | `http-title`, `http-methods`, `http-headers` | Info about HTTP servers                              |
| ftp                  | `ftp-anon`, `ftp-syst`| FTP server info and login checks                                            |
| ssh                  | `ssh-hostkey`, `ssh-auth-methods` | SSH version and login info                                      |

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

