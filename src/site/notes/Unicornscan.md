---
{"dg-publish":true,"permalink":"/unicornscan/"}
---

- [unicornscan \| Kali Linux Tools](https://www.kali.org/tools/unicornscan/?utm_source=chatgpt.com)
- [Reconnaissance with Unicornscan - Hackers Arise](https://hackers-arise.com/reconnaissance-with-unicornscan/?utm_source=chatgpt.com)
- [How to Install Unicornscan & Find Open Ports](https://shouts.dev/articles/install-and-use-unicornscan?utm_source=chatgpt.com)
- [Unicornscan - Port Scanning - Hackerspoilt](https://www.youtube.com/watch?v=X_DdYUeKS-o)

## [[TCP SYN Flag\|SYN]] Scan

```
unicornscan -msf -v 192.168.1.1/24
```

## [[User Datagram Protocol\|UDP]] Scan

```
unicornscan -mU -v 192.168.1.1/24
```

## [[Port\|Port]] Scan
```
unicornscan 192.168.1.1:80,443
```

## Custom Source IP Scan

```
unicornscan -s 192.168.1.100 192.168.1.1:80
```

## [[PCAP\|PCAP]] Saving 


```
unicornscan -w scan_results.pcap -r 1000 -mT 192.168.1.1
```

## [[Operating System\|OS]] Detection

Unicornscan is a network reconnaissance tool that can identify a target machine’s operating system by analyzing the Time to Live ([[Time to Live\|TTL]]) values in the acquired scan results