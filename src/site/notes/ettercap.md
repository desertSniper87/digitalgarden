---
{"dg-publish":true,"permalink":"/ettercap/"}
---

- Ettercap is a network sniffing and MITM attack tool designed to intercept and manipulate network traffic

```bash
ettercap -T -i eth1 -P rand_flood -q -w /tmp/tcpdump3.pcap
```

Launch [[Address Resolution Protocol\|ARP]] spoofing attack

```bash
ettercap -T -i eth1 -M arp
```