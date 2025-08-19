---
{"dg-publish":true,"permalink":"/metasploit-port-scan/"}
---

https://www.cm-alliance.com/cybersecurity-blog/using-metasploit-and-nmap-to-scan-for-vulnerabilities

```msfconsole
db_nmap -sV -A -p 80,22,110,25 192.168.94.134
```