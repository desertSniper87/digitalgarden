---
{"dg-publish":true,"permalink":"/smurf-attack/"}
---


In a Smurf attack, the attacker **spoofs** the **source IP address** with the victim’s IP address and sends a large number of ICMP ECHO request packets to an IP broadcast network
- This causes all the hosts on the broadcast network to respond to the received ICMP ECHO requests
- These responses are sent to the victim’s machine because the IP address was spoofed by the attacker, causing significant traffic to the victim’s machine and ultimately making it crash

![Smurf Attack-1755021169925.webp|674x368](/img/user/Smurf%20Attack-1755021169925.webp)