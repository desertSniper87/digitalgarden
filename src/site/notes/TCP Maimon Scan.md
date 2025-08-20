---
{"dg-publish":true,"permalink":"/tcp-maimon-scan/"}
---


- similar to NULL, FIN and Xmas scan
- The probe used in TCP Maimon scan is FIN/ACK
- to determine if the port is open or closed the RST packet is generated as a response to a probe request
- in many BSD systems the port is open if the packet gets dropped in response to a probe
- Nmap interprets a port as open|filtered when there is no response from the Maimon scan probe even after many retransmissions
- The port is **closed** if the probe gets a response as an **RST packet**
- The port is **filtered** when the [[Ping\|ICMP]] unreachable error (type 3, code 1, 2, 3, 9, 10, or 13) is returned from the target host 

![TCP Maimon Scan-1752904433919.webp|359x387](/img/user/TCP%20Maimon%20Scan-1752904433919.webp)