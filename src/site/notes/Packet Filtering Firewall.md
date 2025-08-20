---
{"dg-publish":true,"permalink":"/packet-filtering-firewall/"}
---


In a packet filtering firewall, each packet is compared with a set of criteria before it is forwarded.
- Depending on the packet and the criteria, the firewall can drop the packet and transmit it or send a message to the originator.
- The rules can include the source and the destination IP address, the source and the destination port number, and the protocol used.
- It works at the internet layer of the TCP/IP model or the network layer of the OSI model.

**Packet filtering firewalls focus on individual packets, analyzing their ==*header*== information to determine the correct direction.** Traditional packet filters make decisions based on the following packet information:
- **Source IP address**: Used to check whether the packet is coming from a valid source. The source IP address can be found in the IP header of the packet.
- **Destination IP address**: Checks if the packet is going to the correct destination and if the destination accepts these types of packets.
- **Source TCP/UDP port**: Used to check the source port of the packet.
- **Destination TCP/UDP port**: Used to monitor the destination port regarding the services to be allowed or denied.
- **TCP flag bits**: Used to check whether the packet has SYN, ACK, or other flags set for the connection to be made.
- **Protocol in use**: Used to check whether the protocol that the packet is carrying should be allowed.
- **Direction**: Used to check whether the packet is entering or leaving the private network. (Inbound / Outbound)
- **[[Network Interface Card\|Interface]]**: Used **to check whether the packet is coming from an unreliable zone**.

![Packet Filtering Firewall Example](path-to-image)