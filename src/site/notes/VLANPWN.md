---
{"dg-publish":true,"permalink":"/vlanpwn/"}
---

VLANPWN is a simple script used for VLAN enumeration and hopping. This tool consists of two Python scripts designed to facilitate VLAN hopping. 

-  `DoubleTagging.py`: This utility is designed to execute a VLAN-hopping attack by injecting a frame with two [[802.1Q\|802.1Q]] tags. In addition, it sends a test ICMP request.


```bash
python3 DoubleTagging.py --interface eth0 --nativevlan 1 --targetvlan 20 --victim <IP> --attacker <IP>
```

-  `DTPHijacking.py`: This script is designed to conduct DTP-switch spoofing/hijacking attacks. It dispatches a malicious DTP-desirable frame and converts the attacker's machine into a trunk channel. This method enables attackers to bypass VLAN network segmentation and gain access to all the VLAN network traffic.

```bash
python3 DTPHijacking.py --interface eth0 
```
