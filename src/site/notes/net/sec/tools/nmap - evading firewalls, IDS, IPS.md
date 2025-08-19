---
{"dg-publish":true,"permalink":"/net/sec/tools/nmap-evading-firewalls-ids-ips/"}
---



```shell-session
sudo nmap 10.129.2.28 -p 21,22,25 -sS -Pn -n --disable-arp-ping --packet-trace
```



Nmap's TCP ACK scan (`-sA`) method is much harder to filter for firewalls and IDS/IPS systems than regular SYN (`-sS`) or Connect scans (`sT`) because they only send a TCP packet with only the `ACK` flag. When a port is closed or open, the host must respond with an `RST` flag



```shell-session
sudo nmap 10.129.2.28 -p 21,22,25 -sA -Pn -n --disable-arp-ping --packet-trace
```


## Decoys

```shell-session
sudo nmap 10.129.2.28 -p 80 -sS -Pn -n --disable-arp-ping --packet-trace -D RND:5
```


#### SYN-Scan of a Filtered Port

```shell-session
sudo nmap 10.129.2.28 -p50000 -sS -Pn -n --disable-arp-ping --packet-trace
```

#### SYN-Scan From DNS Port

```shell-session
sudo nmap 10.129.2.28 -p50000 -sS -Pn -n --disable-arp-ping --packet-trace --source-port 53
```


## DNS

```
nmap -sUVC -p 53,67,123 10.129.101.12 --disable-arp-ping --packet-trace
```


## Test Firewall rules

```shell-session
sudo nmap 10.129.2.28 -n -Pn -p445 -O
```


## Different Source IP

```shell-session
sudo nmap 10.129.2.28 -n -Pn -p 445 -O -S 10.129.2.200 -e tun0
```



## Using [[net/sec/tools/netcat\|netcat]] to connect to filtered port

```shell-session
ncat -nv --source-port 53 10.129.2.28 50000
```