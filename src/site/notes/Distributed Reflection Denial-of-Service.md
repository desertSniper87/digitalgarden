---
{"dg-publish":true,"permalink":"/distributed-reflection-denial-of-service/"}
---

![Distributed Reflection Denial-of-Service-1755023802196.webp|617x340](/img/user/Distributed%20Reflection%20Denial-of-Service-1755023802196.webp)

A distributed reflection DoS (DRDoS) attack, also known as a “spoofed” attack, involves the use of multiple intermediary and secondary machines that contribute to a DDoS attack against a target machine or application
- A DRDoS attack exploits the TCP three-way handshake vulnerability
- This attack involves an attacker machine, intermediary victims (zombies), secondary victims (reflectors), and a target machine
- The attacker launches this attack by sending requests to the intermediary hosts, which in turn reflect the attack traffic to the target
- The process of a DRDoS attack is as follows
- First, the attacker commands the intermediary victims (zombies) to send a stream of packets (TCP SYN) with the primary target’s IP address as the source IP address to other non-compromised machines (secondary victims or reflectors) in order to exhort them to establish a connection with the primary target
- Consequently, the reflectors send a huge volume of traffic (SYN/ACK) to the primary target to establish a new connection with it because they believe the host requested it
- The primary target discards the SYN/ACK packets received from the reflectors because they did not send the SYN packet
- Meanwhile, the reflectors wait for the ACK response from the primary target
- Assuming that the packet was lost, the reflector machines resend SYN/ACK packets to the primary target to establish the connection, until a time-out occurs
- In this manner, the target machine is flooded with a heavy volume of traffic from the reflector machines
- The combined bandwidth of these reflector machines overwhelms the target machine
- A DRDoS attack is an intelligent attack because it is very difficult or even impossible to trace the attacker
- Instead of the actual attacker, the secondary victims (reflectors) seem to attack the primary target directly
- This attack is more effective than a typical DDoS attack because multiple intermediary and secondary victims generate huge attack bandwidth.