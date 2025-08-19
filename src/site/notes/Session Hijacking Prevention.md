---
{"dg-publish":true,"permalink":"/session-hijacking-prevention/"}
---


Manual Method
The manual method involves the use of packet sniffing software such as Wireshark and SteelCentral Packet Analyzer to monitor session hijacking attacks. The packet sniffer captures packets in transit across the network, which is then analyzed using various filtering tools.
Forced ARP Entry
A forced ARP entry involves replacing the MAC address of a compromised machine in the ARP cache of the server with a different one in order to restrict network traffic to the compromised machine. A forced ARP entry should be performed in the case of the following: o Repeated ARP updates o Frames sent between the client and server with different MAC addresses o ACK storms
▪ Automatic Method
The automatic method involves the use of an intrusion detection systems (IDS) and intrusion prevention systems (IPS) to monitor incoming network traffic. If the packet matches any of the attack signatures in the internal database, the IDS generates an alert, whereas the IPS blocks the traffic from entering the database.
Module