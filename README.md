# Networkd

***Netstat***
```bash
netstat -rn // will show us the networks accessible
```
***Netcat ncat or nc***
```bash
nc IP PORT
nc -lnvp PORT 
```
| Option          | Description                                                            |
|-----------------|------------------------------------------------------------------------|
| `-l`            | Listen mode (waits for incoming connection)                            |
| `-v`            | Verbose mode (prints connection details)                               |
| `-n`            | Do not resolve DNS (use raw IP addresses)                              |
| `-p <port>`     | Specify source port (used with `-l`)                                   |
| `-e <cmd>`      | Execute a command after connection (⚠️ often disabled for security)    |
| `-c <cmd>`      | Same as `-e`, but uses internal shell (less common)                    |
| `-u`            | Use UDP instead of TCP                                                 |
| `-z`            | Zero-I/O mode (used for port scanning)                                 |
| `-w <sec>`      | Set connection timeout in seconds                                      |
| `-k`            | Keep listening after a connection closes (server mode)                 |
| `--source-port` | Change the source port (ncat only -p on the others                     |

***Dig***
```bash
dig <domain>
```
| Option        | Description                                                      | Exemple                            | 
|---------------|------------------------------------------------------------------|------------------------------------|                
| `@server`     | Spécifie le serveur DNS à interroger                              | `dig @8.8.8.8 example.com`         |                   
| `-t type`     | Type d’enregistrement DNS à demander (A, MX, NS, TXT…)           | `dig example.com -t MX`            |
| `+short`      | Affiche une sortie simplifiée (juste les réponses)                  | `dig example.com +short`           |
| `+noall`      | Désactive toutes les sections sauf celles demandées              | `dig example.com +noall +answer`   |
| `+answer`     | Affiche uniquement la section réponse                              | `dig example.com +answer`          |
| `+stats`      | Affiche les statistiques de la requête DNS                         | `dig example.com +stats`           |
| `+trace`      | Trace la résolution DNS complète (serveurs racine à autoritaire) | `dig example.com +trace`           |
| `-x`          | Effectue une recherche inverse (résolution PTR)                   | `dig -x 8.8.8.8`                   |
| `+dnssec`     | Demande les enregistrements DNSSEC                               | `dig example.com +dnssec`          |
| `+time=N`     | Définit le timeout en secondes (par défaut 5 secondes)            | `dig example.com +time=10`         |
| `+retry=N`    | Nombre de tentatives en cas d’échec (par défaut 3)               | `dig example.com +retry=2`         |
| `any`         | All records                                                      | `dig any <domain>`                 |

***Transfert method***
```bash
python3 -m http.server 8000 // server
wget http://<IP>:<PORT>/file // Download method 1
curl http://<IP>:<PORT>/<File> -o <Outputfilename> // Download method 2
// Base 64 method
base64 -w 0 File // Encoding -w 0 Everything on one line
echo <Line> | base64 -d > File
```
***SSH***
```bash
ssh <USER>@<IP> <OPTIONS>
ssh root@10.10.10.10 -i id_rsa // chmod 600 on key
scp <File> <User>@<RemoteHost>:/PATH/FILE
scp <User@<RemoteHost>:/PATH/FILE ./FILENAME
```

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

***SMB***
```bash
smbclient -OPTIONS \\TARGET\DIR
smbclient -U bob -N -L \\\\TARGET // -N Anonymous -L list -U user
```
| Command       | Description                                    |
|---------------|------------------------------------------------|
| `ls`          | List files and directories in the current share |
| `cd <dir>`    | Change directory on the remote share           |
| `get <file>`  | Download a file from the share                   |
| `put <file>`  | Upload a file to the share                       |
| `mget <files>`| Download multiple files                          |
| `mput <files>`| Upload multiple files                            |
| `del <file>`  | Delete a file on the share                       |
| `mkdir <dir>` | Create a directory on the share                |
| `rmdir <dir>` | Remove a directory on the share                |
| `pwd`         | Print the current directory on the share       |
| `exit`        | Disconnect from the SMB share                  |
| `help`        | Show available commands                        |

***SNMP***
```bash
snmpwalk -version -communitychain <TARGET> <OID>
snmpwalk -v 2c -c public 10.129.42.253 1.3.6.1.2.1.1.5.0 // -v version -c community chain
onesixtyone -c <DICT> <TARGET> //  brute force community string name : -c Dictionary file 
```
| OID Prefix              | OID Example               | Name/Description                     | Notes                         |
|------------------------|--------------------------|---------------------------------------|-------------------------------|
| 1.3.6.1.2.1.1          | 1.3.6.1.2.1.1.1.0        | sysDescr - System Description         | General system info           |
|                        | 1.3.6.1.2.1.1.3.0        | sysUpTime - System uptime             | Time since last reboot        |
|                        | 1.3.6.1.2.1.1.4.0        | sysContact - Contact info             | Admin contact                 |
|                        | 1.3.6.1.2.1.1.5.0        | sysName - Hostname                    | System name                   |
|                        | 1.3.6.1.2.1.1.6.0        | sysLocation - Physical location       | Device location               |
| 1.3.6.1.2.1.2          | 1.3.6.1.2.1.2.2.1.2.x    | ifDescr - Interface description       | Interface names               |
|                        | 1.3.6.1.2.1.2.2.1.8.x    | ifOperStatus - Interface status       | up(1), down(2), testing(3)    |
| 1.3.6.1.2.1.25         | 1.3.6.1.2.1.25.1.1.0     | hrSystemUptime - Host uptime          | Host resources MIB            |
|                        | 1.3.6.1.2.1.25.2.3.1.6.x | hrStorageUsed - Storage used          | Disk/memory usage             |
|                        | 1.3.6.1.2.1.25.3.3.1.2.x | hrProcessorLoad - CPU load            | Host CPU load                 |
| 1.3.6.1.4.1            | Vendor-specific MIBs      | Various OIDs depending on vendor      | E.g., Cisco, HP, Juniper      |

***Nmap***
```bash
nmap -OPTIONS IP
// Exemples
// Host discovery
nmap 10.129.2.0/24 -sn -oA tnet | grep for | cut -d" " -f5 // scan for hosts up
nmap -sn -oA tnet -iL hosts.lst | grep for | cut -d" " -f5 // use a list
nmap -sn -PE -oA Host <IP>/24 // Force -sn to use only ICMP with -PE
nmap -sn -PE --disable-arp-ping <IP> // Nmap uses arp ping on local network by default even with -PE --disable-arp-ping = force to not use ARP
// Scans
nmap <IP> -p 21 --packet-trace -Pn -n --disable-arp-ping // default scan -sS if sudo and -sT if not
// Format Output
xsltproc <File.xml> -o File.html // transform xml output in html
```
| Option          | Description                                                     |
|-----------------|-----------------------------------------------------------------|
| `-e`            | Sends all requests through the specified interface ex: -e tun0   | 
| `-S`            | Specifies the source IP address                                  |
| `--source-port` | Change the source port                                          | 
| `-sS`           | TCP SYN scan (stealth scan)                                     |
| `-sT`           | TCP connect scan (full connection)                              |
| `-sU`           | UDP scan                                                        |
| `-sSU`          | -sU and -sS combined                                            |
| `-sA`           | Ack scan (better evasion)                                       |
| `-p`            | Specify ports to scan (e.g., -p 80,443,1-100)                   | 
| `-p-`           | Scan all TCP ports (1 to 65535)                                 |
| `-F`            | Fast scan: scan only the most popular ports                     |
| `-sV`           | Service version detection                                       |
| `-sC`           | Run default scripts (Nmap Scripting Engine - NSE)               |
| `-A`            | Full scan: OS detection, version detection, scripts, traceroute |
| `-T0 to -T5`    | Set scan speed/aggressiveness (-T0 slowest, -T5 fastest)        |
| `-iL file`       | Input List (ex2)                                                |
| `-O`            | OS detection scan                                               |
| `-oN`           | Save output to normal text file                                  |
| `-oX`           | Save output to XML format                                       |
| `-oG`           | Save output in grepable format (for easier parsing)             |
| `-oA`           | All the format                                                  |
| `-sn`           | Ping scan only ICMP or Syn/ack or ARP on local                  |                                               
| `-n`            | No DNS resolution (faster scan)                                 |
| `-Pn`           | Skip host discovery (treat host as up)                          |
| `-PE`           | Force ICMP Echo requests                                        |
| `--script`      | Specify NSE scripts to run                                      |
| `-sn`           | Ping scan: only detect active hosts, no port scan               |
| `--open`        | Only report open ports                                          |
| `--packet-trace`| Shows all packets sent and received                             |
| `--reason`      | Displays the reason for specific result                          |
|`--disable-arp-ping` | Disable Arp ping (default host discovery on local network   |
|`-D RND:5`       | Decoy RND:5 == 5 random ip problem not alive : -D ip,ip,trueip,ip |
|`--dns-server <ns>` | Specifies the DNS                                             |

| Script Category      | Example Script        | Description                                                                 |
|----------------------|-----------------------|-----------------------------------------------------------------------------|
| default              | -                     | Default script set (used with `-sC`)                                        |
| safe                 | -                     | Scripts considered non-intrusive                                            |
| vuln                 | `vulners`, `http-vuln*`| Checks for known vulnerabilities (CVEs, exploits)                          |
| auth                 | `ftp-anon`, `http-auth`| Authentication-related checks (e.g., anonymous login)                      |
| brute                | `ssh-brute`, `ftp-brute`| Performs brute force attacks on various protocols                         |
| discovery            | `broadcast-dhcp-discover`, `dns-brute` | Gathers information from the network                       |
| dos                  | `http-slowloris`      | Denial of service testing (⚠️ dangerous)                                   |
| exploit              | `http-shellshock`, `ftp-proftpd-backdoor` | Attempts known exploits (⚠️ dangerous)                 |
| malware              | `http-malware-host`, `irc-unrealircd-backdoor` | Detects backdoors or malware-infected services     |
| safe version scan    | `banner`, `http-title`| Basic fingerprinting/info gathering                                         |
| smb                  | `smb-enum-shares`, `smb-os-discovery` | SMB-related information and vulnerability checks            |
| ssl                  | `ssl-cert`, `ssl-enum-ciphers` | Checks for SSL/TLS certificate info and weak ciphers               |
| http                 | `http-title`, `http-methods`, `http-headers` | Info about HTTP servers                              |
| ftp                  | `ftp-anon`, `ftp-syst`| FTP server info and login checks                                            |
| ssh                  | `ssh-hostkey`, `ssh-auth-methods` | SSH version and login info                                      |

| State                   | Description                                                                                                                                                  |
|-------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `open`                  | The connection to the scanned port has been established. This can include TCP connections, UDP datagrams, or SCTP associations.                              |
| `closed`                | The port is closed: the TCP response contains an RST flag. This scan result can also help determine if the target is alive.                                  |
| `filtered`              | Nmap cannot determine whether the port is open or closed because no response was received or an error was returned (likely due to firewall filtering).       |
| `unfiltered`            | Only occurs during a TCP-ACK scan. The port is accessible, but it cannot be determined whether it is open or closed.                                         |
| `open\|filtered`        | No response received for the port. It could be open or filtered, possibly protected by a firewall or packet filter.                                          |
| `closed\|filtered`      | Only appears in IP ID idle scans. It is not possible to determine if the port is closed or filtered by a firewall.                                           |


***Ports***

| Port | Protocole | Service         | Description                                                            | Info                                          |
|------|-----------|-----------------|------------------------------------------------------------------------|-----------------------------------------------|
| 20/21| TCP	     | FTP             | Uncrypted file transfert                                               |                                               |
| 22   | TCP       | SSH             | Secure remote access                                                   |                                               |
| 23   | TCP       | Telnet          | Uncrypted remote access                                                |                                               |
| 25   | TCP       | SMTP            | Sending emails (unencrypted by default)                                |                                               |
| 53   | UDP/TCP   | DNS             | Domain name resolution                                                 |                                               |
| 80   | TCP       | HTTP            | Unencrypted web traffic                                                |                                               |
| 135  | TCP       | RPC             | Remote processus call                                                  |                                               |
| 139  | TCP       | Netbios         | Old Samba                                                              |                                               |
| 161  | TCP/UDP   | SNMP            | Used for network management (v1/v2c are unencrypted)                   |                                               |
| 443  | TCP       | HTTPS           | Encrypted web traffic (SSL/TLS)                                        |                                               |
| 445  | TCP       | SMB             | File sharing protocol (commonly targeted                               |                                               |
| 3389 | TCP       | RDP             | Remote desktop access (often targeted, requires strong authentication) | xfreerdp /v:ip /u:user /p:password ou /prompt |

# Web
***Gobuster***
```bash
gobuser <mode> -OPTIONS 
gobuster dir -u http://10.10.10.121/ -w /usr/share/seclists/Discovery/Web-Content/common.txt -x php,html // mode: dir -u URL -w Wordlist -x specifie l'extension de fichier php html etc..
gobuster dns -d <TARGET> -w /usr/share/SecLists/Discovery/DNS/namelist.txt // mode dns -d dnsname -w Wordlist
```

## Banner grabing
***Curl***
```bash
curl -IL <URL>  // -I HEADERS ONLY -L Accept redirection
```

***whatsweb***
```bash
Whatweb <target> or <target/range>
```
# Exploit
[Payloads](payloads.md) - [Privilege Escalation](privilege.md) = [Enumeration](enum.md)

***finding***
```bash
searchsploit openssh 7.2 // exploitdb packet
```
