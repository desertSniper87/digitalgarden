---
{"dg-publish":true,"permalink":"/ping-of-death/"}
---


In a Ping of Death (PoD) attack, an attacker attempts to crash, destabilize, or freeze the target system or service by sending malformed or oversized packets using a simple ping command
- Suppose an attacker sends a packet with a **size of 65,538 bytes to the target web server**
- This size exceeds the size limit prescribed by [[IP fragmentation\|RFC 791]] IP, which is 65,535 bytes
- The reassembly process performed by the receiving system might cause the system to crash
- In such attacks, the attacker’s identity can be easily spoofed, and the attacker might not need detailed knowledge of the target machine, except its IP address.


## Using [[hping3\|hping3]]

```bash
hping3 -S 192.168.60.130 -a 192.168.60.135 -p 21 --flood
```


```
sudo hping3 -d 65538 -S -p 21 --flood 192.168.60.130
```