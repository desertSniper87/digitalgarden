---
{"dg-publish":true,"permalink":"/net/sec/tools/nmap/"}
---

- [Insecure.Org - Nmap Free Security Scanner, Tools & Hacking resources](https://insecure.org)
- [[nmap - output\|nmap - output]]
- [[nmap flags\|nmap flags]]


## Docs

- [Nmap Cheat Sheet](https://www.stationx.net/nmap-cheat-sheet/)

### Reference

1. [Site Unreachable](https://linuxhint.com/nmap-port-scanning-security/)

_Insane speed, no DNS resolution and port specification_
```bash
nmap -T5- -n -p1-65535 192.168.0.102
```

_Insane speed, no host discovery, no DNS resolution and all ports_

```bash
nmap -T5- -Pn -n -p- 192.168.0.102
```

_No host discovery, Stealth Scan and specify ports_
```bash
nmap -Pn -sS -p 1-65535 10.10.11.202
```

_Script, Stealth Scan, Version Detection and verbose output_
```bash
nmap -sCVS -vvv 10.10.11.202
```
_Stealth Scan, Version Detection, no host discovery and no DNS resolution_

```bash
nmap -sS -sV -Pn -n 192.168.60.130
```

_Aggresive Scan, no host discovery and no DNS resolution_

```bash
nmap -A -Pn -n 192.168.130.60
```


_Version detection, no host discovery, vulnerability script and no DNS resolution_

```bash
nmap -sV -Pn --script vuln -n 192.168.60.130
```


```bash
nmap -Pn -n -sV 10.10.159.242
```

```bash
nmap -Pn -n -T5 -p- 10.10.69.159
```
## Scanning Subnets

```
nmap -sn 192.168.1.0/24
```

```bash
nmap 10.129.2.0/24 -sn -oA tnet | grep for | cut -d" " -f5 > hosts.lst
```

## Hosts file

_reason gives why the port is up_

```shell-session
nmap -iL hosts.lst -sn -oA host -PE --reason
```

## Trace Packets using nmap

```shell-session
nmap 10.129.2.28 -sU -Pn -n --disable-arp-ping --packet-trace -p 137 --reason
```

# Host Discovery Techniques

- [Host Discovery Techniques \| Nmap Network Scanning](https://nmap.org/book/host-discovery-techniques.html)


```ad-info
- **[[Ping\|ICMP]] Ping Scan** (-PE, -PP, -PM): Nmap sends ICMP echo requests, timestamp requests, or netmask requests to determine if a host is online. If the target responds, it confirms the host is reachable.
- **TCP Ping Scan** (-PS, -PA, -PU, -PY): Instead of ICMP, Nmap sends TCP SYN or ACK packets to specific ports. If the target replies (e.g., with a SYN-ACK), it indicates the host is active. This method is useful when ICMP is blocked by firewalls.
- **Ping Scan** (-sn): This disables port scanning and only performs host discovery using the selected method (ICMP, TCP, or UDP).
- ARP Scan (-PR): Instead of sending ICMP or TCP packets, Nmap sends **ARP requests** to determine if a host is online.
```


# [[Ping\|Ping]]

## [[Hardware/Laptop/arp ping scan\|arp ping scan]]

**On most LANs, especially those using private address ranges granted by [[RFC 1918\|RFC 1918]]**
```
nmap -sn -PR 192.168.60.130
```

## [[Ping\|ICMP]] Ping Scan

Like `-sn` but only [[ICMP Echo request\|ICMP Echo request]]s are used

```bash
nmap -sn -PE 192.168.60.130
```

## [[Ping\|ICMP]] Timestamp Ping 

- Nmap sends an **ICMP timestamp request** to the target.
- If the target responds with an **ICMP timestamp reply**, it confirms the host is online
- Useful when standard ICMP Echo Requests (`-PE`) are blocked but timestamp requests are allowed.
```bash
nmap -sn -PP 192.168.60.130
```

## [[Ping|ICMP]] Address mask Ping


- Address mask ping is another alternative to the traditional ICMP ECHO ping
- Attackers send an **ICMP address mask** query to the target host **to acquire information related to the [[Subnet Mask\|Subnet Mask]]**
- The address mask response from the destination host is conditional
	- it may or may not respond with the appropriate subnet value **depending on its configuration** by the **administrator** at the target’s end
- This type of ping method is also effective in identifying the **active hosts** similarly to the ICMP timestamp ping
- the -PM option is used to perform an ICMP address mask ping scan.

```bash
nmap -sn -PM 10.10.1.13
```

## [[net/protocols/Transmission Control Protocol\|TCP]] SYN Ping Scan

```bash
nmap -sn -PS 192.168.60.130
```

## [[User Datagram Protocol\|UDP]] Ping Scan

```bash
nmap -sn -PU 192.168.60.130
```

## Scan top 10 ports

```shell-session
nmap 10.129.2.28 --top-ports=10
```
## [[Traceroute\|Traceroute]]

```bash
nmap -sn --traceroute 192.168.60.130
```

## Slow Comprehensive Scan

[[shodan\|Shodan]] is required
```bash
nmap -sS -sU -T4 -A -v -PE -PP -PS80,443 -PA3389 -PU40125 -PY -g 53 --script "default or (discovery and safe)" 192.168.60.129-130
```


## Scanning [[Windows\|Windows]] machine

1. [network - Nmap says host down when host is up - Information Security Stack Exchange](https://security.stackexchange.com/questions/124394/nmap-says-host-down-when-host-is-up)


### Timing flags (**-T**)

, **Nmap uses a balanced timing option (-T4)** which is suitable for most situations. However, you can try increasing the timing option to a higher value, such as -T3 or -T2, to speed up the scan.

The `-T` flag in `nmap` is used to specify the "timing template" for the scan. The timing template determines how aggressively nmap will scan the target host, with higher values indicating more aggressive (and potentially faster) scanning. ==**_The `-T4` and `-T5` options correspond to the "aggressive" and "insane" timing templates_**, ==respectively, and are the most aggressive options available.

---

```
nmap -p 1-100 192.168.64.5
```

```
nmap -p 22 192.168.64.5
```

## OS Detection

```
sudo nmap -O 192.168.64.5
```

## UDP

```bash
nmap -sU -p- TARGETIP
```

### UDP port scanning

```bash
nmap -sU -p 8080 TARGETIP
```

## [[net/windows/Server Message Block\|Server Message Block]]

```bash
nmap --script smb-os-discovery TARGET
```

```bash
nmap --script smb-enum-users TARGET
```


## Saving to file


```bash
nmap -sV -Pn -F -n -oN scan1.txt 192.168.60.130
```


## Default Options

- for **Privledged** users, the default option is the `-sS` scan ([[nmap - syn scan\|nmap - syn scan]])
- for **unpriledged** users, the default option is the `-sT` scan (([[net/sec/tools/nmap - Full-Open Scan\|Full Open Scan]]))