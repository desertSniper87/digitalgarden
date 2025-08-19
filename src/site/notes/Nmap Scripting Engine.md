---
{"dg-publish":true,"permalink":"/nmap-scripting-engine/"}
---


| Category         | Description                                                                                                                             |
| ---------------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| auth             | Determination of authentication credentials.                                                                                            |
| broadcast        | Scripts, which are used for host discovery by broadcasting and the discovered hosts, can be automatically added to the remaining scans. |
| brute            | Executes scripts that try to log in to the respective service by brute-forcing with credentials.                                        |
| default          | Default scripts executed by using the -sC option.                                                                                       |
| discovery        | Evaluation of accessible services.                                                                                                      |
| dos              | These scripts are used to check services for denial of service vulnerabilities and are used less as it harms the services.              |
| exploit          | This category of scripts tries to exploit known vulnerabilities for the scanned port.                                                   |
| external         | Scripts that use external services for further processing.                                                                              |
| fuzzer           | This uses scripts to identify vulnerabilities and unexpected packet handling by sending different fields, which can take much time.     |
| intrusive        | Intrusive scripts that could negatively affect the target system.                                                                       |
| malware          | Checks if some malware infects the target system.                                                                                       |
| safe             | Defensive scripts that do not perform intrusive and destructive access.                                                                 |
| version          | Extension for service detection.                                                                                                        |
| vuln             | Identification of specific vulnerabilities.                                                                                             |
| smtp-commands    |                                                                                                                                         |
| banner           |                                                                                                                                         |
| http-waf-detect  | Detects [[Web Application Firewall\|WAF]]                                                                                               |
| http-trace       | Sends HTTP TRACE request that shows if the method is enabled or not.                                                                    |
| smb-os-discovery |                                                                                                                                         |
| http-title       | Webserver banner grabbing                                                                                                               |
| sniffer-detect   | check whether a system on a local Ethernet has its network card in [[Promiscuous Mode\|promiscuous mode]].                                                |

## Run with all scripts

```bash
nmap -sC 10.129.200.185 -p 80 --script auth,broadcast,brute,fuzzer,intrusive,version,vuln,malware,exploit,external,dos
```

```bash
nmap -sC 10.129.201.89 -p 8080 --script auth,intrusive,version,vuln,malware,exploit,banner
```

## Wildcard

```bash
nmap -p 80 -sV --script=http-vuln* http://www.moviescope.com
```