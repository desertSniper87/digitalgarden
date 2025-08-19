---
{"dg-publish":true,"permalink":"/session-hijacking/"}
---


- Attacker hijacks valid [[net/protocols/Transmission Control Protocol\|TCP/IP]] communication session.

![Pasted image 20250615180918.png](/img/user/Pasted%20image%2020250615180918.png)


Session hijacking can be divided into three broad phases. 

## Tracking the connection

The attacker uses a [[network sniffer\|network sniffer]] to track a victim and host or uses a tool such as [[net/sec/tools/nmap\|nmap]] to scan the network for a target with a TCP sequence that is easy to predict
- After identifying a victim, the attacker captures the sequence and acknowledgment numbers of the victim because TCP checks these numbers
- The attacker then uses these numbers to construct packets.

## Desynchronizing the connection

A desynchronized state occurs when a connection between a target and host is established, or stable with no data transmission or the server’s sequence number is not equal to the client’s acknowledgment number, or vice versa.

To desynchronize the connection between the target and host, the attacker must change the sequence number or acknowledgment number (SEQ/ACK) of the server
- For this purpose, the attacker sends null data to the server; consequently, the server’s SEQ/ACK numbers advance, while the target machine does not register the increment
- For example, before desynchronization, the attacker monitors the session without any interference, following which they send a large amount of null data to the server
- These data change the ACK number on the server without affecting anything else, thereby desynchronizing the server and target.

Another approach is to send a reset flag to the server to break the connection on the server side
- Ideally, this occurs in the early setup stage of the connection
- The attacker’s goal is to break the connection on the server side and create a new connection with a different sequence number
- The attacker waits for a SYN/ACK packet from the server to the host
- On detecting a packet, the attacker immediately sends an RST packet and a SYN packet with identical parameters, such as a port number with a different sequence number, to the server
- The server, on receiving the RST packet, closes the connection with the target and initiates another one based on the SYN packet but with a different sequence number on the same port
- After opening a new connection, the server sends a SYN/ACK packet to the target for acknowledgement
- The attacker detects (but does not intercept) this packet and sends an ACK packet to the server
- Now, the server is in the established state
- The aim is to keep the target conversant and ensure that it switches to the established state on receiving the first SYN/ACK packet from the server
- Consequently, both the server and target are desynchronized but in an established state
- An attacker can also use a FIN flag, but this will make the server respond with an ACK packet, thus revealing the attack through an ACK storm
- The attack is revealed because of a flaw in this method of hijacking a TCP connection
- While receiving an unacceptable packet, the host acknowledges it by sending the expected sequence number
- This unacceptable packet generates an ACK packet, thereby creating an endless loop for every data packet
- The mismatch in SEQ/ACK numbers results in excess network traffic

with both the server and target attempting to verify the correct sequence
- Because these packets carry no data, retransmission does not occur if the packet is lost
- However, because TCP uses IP, the loss of a single packet ends the unwanted conversation between the server and target.

An attacker can add a desynchronizing stage to the hijack sequence to deceive the target host
- Without desynchronizing, the attacker injects data into the server while keeping their identity hidden by spoofing an IP address
- However, the attacker should ensure that the server responds to the target host as well.

## Injecting the attacker's packet

Once the attacker has interrupted the connection between the server and target, they can either inject data into the network or actively participate as the man in the middle, passing data from the target to the server and vice-versa while reading and injecting data at will.
