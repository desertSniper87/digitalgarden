---
{"dg-publish":true,"permalink":"/nmap-flags/"}
---


## nmap flags

| Flags              | Description                                             |                                                                                |
| ------------------ | ------------------------------------------------------- | ------------------------------------------------------------------------------ |
| --disable-arp-ping | Disables ARP ping                                       |                                                                                |
| --open             |                                                         |                                                                                |
| --packet-trace     | Trace Packet                                            |                                                                                |
| --top-ports        |                                                         |                                                                                |
| -A                 | Aggresive Mode                                          | OS detection, version detection, script scanning, and traceroute.<br>          |
| -F                 | Fast Scan                                               | Scans top 100 ports                                                            |
| -O                 | [[OS\|OS]] Detection                                        |                                                                                |
| -PE                | [[Ping\|Ping]] Echo Request                                   | ping scan by using 'ICMP Echo requests' (for larger networks)                  |
| -PR                | [[Address Resolution Protocol\|ARP]] Request            | for local network scans where ARP is supported                                 |
| -Pn                | disables host discovery                                 | For escaping [[Windows Defender\|Windows Defender]], -P0 in older versions                       |
| -T                 | Timing                                                  | 1-5                                                                            |
| -iL                |                                                         | Read target IPs/ranges from the file hosts.lst.                                |
| -n                 | Never do [[Domain Name System\|Domain Name System]] Resolution              |                                                                                |
| -oA tnet           |                                                         | Output in **all** formats (normal, XML, and grepable) with base filename tnet. |
| -p                 | Ports 1-65535                                           |                                                                                |
| -sC                | Script Scan                                             | Default scripts if no script is provided                                       |
| -sN                | Null TCP Scan<br>                                       |                                                                                |
| -sS                | [[net/protocols/Transmission Control Protocol\|Transmission Control Protocol]] SYN scan              | Stealth Scan ([[net/sec/tools/nmap - Stealth Scan\|Half Open Scan]])                         |
| -sT                | TCP [[net/sec/tools/nmap - Full-Open Scan\|nmap - Full-Open Scan]] Scan                      | Full TCP Scan ([[net/sec/tools/nmap - Full-Open Scan\|Full Open]])                           |
| -sU                | [[User Datagram Protocol\|User Datagram Protocol]] Scan                         |                                                                                |
| -sV                | Version Detection                                       |                                                                                |
| -sn                | Disable Port Scanning                                   |                                                                                |
| -v                 | Verbose Mode                                            |                                                                                |
| -vvv               | Increased verbosity level                               |                                                                                |
| -PS                | TCP SYN Ping                                            |                                                                                |
| -PM                | ICMP Address Mask Ping Scan                             |                                                                                |
| -PA                | TCP ACK Ping Scan                                       |                                                                                |
| -PO                | IP Protocol Ping Scan                                   |                                                                                |
| -sZ                |                                                         |                                                                                |
| -sX                | [[Xmas Scan\|Xmas Scan]]                                           |                                                                                |
| -sA                | Ack flag probe scan                                     |                                                                                |
| -f                 | Fragmented Packets (fragscan)                           | split the IP packet into tiny fragment packets                                 |
| -g                 | Source port                                             |                                                                                |
| -mtu               | [[Maximum transmission unit\|MTU]]                      |                                                                                |
| -D                 | Decoy [[IP Address\|IP]]                                |                                                                                |
| --spoof-mac        | Spoof [[MAC Address\|MAC Address]]                                   | --spoof-mac 0 (Randomize [[MAC Address\|MAC]])                                 |
| -sY                | [[Stream Control Transport Protocol\|SCTP]] Init Scan   |                                                                                |
| -sZ                | [[Stream Control Transport Protocol\|SCTP]] Cookie Scan |                                                                                |
| -sL                | List Targets in range                                   |                                                                                |
| -sM                | [[TCP Maimon Scan\|TCP Maimon Scan]]                                     |                                                                                |
| -sF                | [[TCP - Termination\|FIN]] Scan                         |                                                                                |
| -S                 | Spoof Source IP Address                                 |                                                                                |
