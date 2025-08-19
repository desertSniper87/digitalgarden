---
{"dg-publish":true,"permalink":"/net/sec/tools/nmap-full-open-scan/"}
---

When two parties establish a connection using TCP, they perform a three-way handshake. A three-way handshake starts the connection and exchanges all the parameters needed for the two parties to communicate. TCP uses a three-way handshake to establish a new connection. Initially, the client-side connection is in the closed state and the server-side in the listening state. The client initiates the connection by sending the initial sequence number (ISN) and setting the SYN flag. The client is now in the SYN-SENT state. When the server receives this packet, it acknowledges the client sequence number and sends its own ISN with the SYN flag set. The server’s state is now SYN-RECEIVED. On receipt of this packet, the client acknowledges the server sequence number by incrementing it and setting the ACK flag. The client is now in the established state. At this point, the two machines have established a session and can communicate. On receiving the client’s acknowledgement, the server enters the established state and sends an acknowledgment, incrementing the client’s sequence number. The connection can be closed either by using the FIN or RST flag or through a time out. If the RST flag of a packet is set, the receiving host enters the CLOSED state and frees all resources associated with this connection. This leads to the connection drop of any additional incoming packets. If the packet is sent with the FIN flag turned on, the receiving host closes the connection because it enters the CLOSE-WAIT state. The packets sent by the client are accepted in an established connection if the sequence number is within the range and follows its predecessor. If the sequence number is beyond the range of the acceptable sequence numbers, it drops the packet and sends an ACK packet using the expected sequence number. 


![nmap - Full-Open Scan-1752690940365.webp|532x396](/img/user/nmap%20-%20Full-Open%20Scan-1752690940365.webp)

```bash
nmap -sT 192.168.64.5 > tcp.connect.txt
```