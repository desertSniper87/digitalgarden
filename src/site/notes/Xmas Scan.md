---
{"dg-publish":true,"permalink":"/xmas-scan/"}
---


- Xmas scan is a type of inverse TCP scanning technique with the following flags set to send a TCP frame to a remote device:
	- FIN
	- URG
	- PUSH 
- If the target has opened the port
	- no response will be received from the remote system
- If the target has **closed the port**
	- A reply with an **RST** will be received from the  remote system 
- You can use this port scanning technique to scan large networks and find which host is up and what services it is offering
- This technique describes all TCP flag sets
- When all flags are set
	- some systems hang; hence
		- the flags are often set in the nonsense pattern URG-PSH-FIN
- Attackers use the TCP Xmas scan to determine if ports are closed on the target machine via the RST packet
- This scan only works when systems are compliant with [[net/protocols/Transmission Control Protocol\|RFC 793]]-based [[net/protocols/Transmission Control Protocol\|TCP]]/IP implementation
- **It will not work against any current version of Microsoft Windows.**