---
{"dg-publish":true,"permalink":"/net/protocols/transmission-control-protocol/"}
---

- [Transmission Control Protocol](https://en.wikipedia.org/wiki/Transmission_Control_Protocol)
- [RFC 793: Transmission Control Protocol](https://www.rfc-editor.org/rfc/rfc793)


## Comparison with [[net/protocols/Hypertext Transfer Protocol\|Hypertext Transfer Protocol]]

- [The Difference Between HTTP and TCP](https://www.goanywhere.com/blog/http-vs-tcp-whats-the-difference#:~:text=TCP%20contains%20information%20about%20what,data%20in%20the%20stream%20contains.)


## TCP Header

![tcp-header.webp|415x140](/img/user/tcp-header.webp)

### IP header

![ip-header.webp|503x230](/img/user/ip-header.webp)

[IP Header]
  └─ Source IP: 192.168.1.10
  └─ Destination IP: 192.168.1.20

[TCP Header]
  └─ Source Port: 443
  └─ Destination Port: 51515

## TCP Flags

- URG
	- The **URG** Flag indicates that the data being sent is urgent and should be prioritized
- FIN
    - The **FIN** flag is used to *gracefully terminate* a TCP connection
- RST
	- The **RST** flag is used to *immediately terminate* a connection

## 3 Way Handshake

- SYN
- SYN+ACK
- ACK

### Termination

- FIN
- ACK+FIN
- ACK

## TCP Based Protocols
| **Protocol**                                              | **Acronym**  | **Port**         | **Description**                                                                                                                                                                    |
| --------------------------------------------------------- | ------------ | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [[Telnet\|Telnet]]                                                | `Telnet`     | `23`             | Remote login service                                                                                                                                                               |
| [[sre/Tools/Secure Shell\|Secure Shell]]                                          | `SSH`        | `22`             | Secure remote login service                                                                                                                                                        |
| [[net/protocols/Simple Network Management Protocol\|Simple Network Management Protocol]]                    | `SNMP`       | `161-162`        | Manage network devices                                                                                                                                                             |
| [[net/protocols/Hypertext Transfer Protocol\|Hypertext Transfer Protocol]]                           | `HTTP`       | `80`             | Used to transfer webpages                                                                                                                                                          |
| [[net/protocols/HTTPS\|Hyper Text Transfer Protocol Secure]]            | `HTTPS`      | `443`            | Used to transfer secure webpages                                                                                                                                                   |
| Domain Name System                                        | `DNS`        | `53`             | Lookup domain names                                                                                                                                                                |
| File Transfer Protocol                                    | `FTP`        | `20-21`          | Used to transfer files                                                                                                                                                             |
| Trivial File Transfer Protocol                            | `TFTP`       | `69`             | Used to transfer files                                                                                                                                                             |
| Network Time Protocol                                     | `NTP`        | `123`            | Synchronize computer clocks                                                                                                                                                        |
| Simple Mail Transfer Protocol                             | `SMTP`       | `25`             | Used for email transfer                                                                                                                                                            |
| Post Office Protocol                                      | `POP3`       | `110`            | Used to retrieve emails                                                                                                                                                            |
| Internet Message Access Protocol                          | `IMAP`       | `143`            | Used to access emails                                                                                                                                                              |
| [[net/windows/Server Message Block\|Server Message Block]]                                  | `SMB`        | `445`            | Used to transfer files                                                                                                                                                             |
| Network File System                                       | `NFS`        | `111`, `2049`    | Used to mount remote systems                                                                                                                                                       |
| Bootstrap Protocol                                        | `BOOTP`      | `67`, `68`       | Used to bootstrap computers                                                                                                                                                        |
| Kerberos                                                  | `Kerberos`   | `88`             | Used for authentication and authorization                                                                                                                                          |
| Lightweight Directory Access Protocol                     | `LDAP`       | `389`            | Used for directory services                                                                                                                                                        |
| Remote Authentication Dial-In User Service                | `RADIUS`     | `1812`, `1813`   | Used for authentication and authorization                                                                                                                                          |
| Dynamic Host Configuration Protocol                       | `DHCP`       | `67`, `68`       | Used to configure IP addresses                                                                                                                                                     |
| [[Remote Desktop Protocol\|Remote Desktop Protocol]]                               | `RDP`        | `3389`           | Used for remote desktop access                                                                                                                                                     |
| Network News Transfer Protocol                            | `NNTP`       | `119`            | Used to access newsgroups                                                                                                                                                          |
| Remote Procedure Call                                     | `RPC`        | `135`, `137-139` | Used to call remote procedures                                                                                                                                                     |
| Identification Protocol                                   | `Ident`      | `113`            | Used to identify user processes                                                                                                                                                    |
| Internet Control Message Protocol                         | `ICMP`       | `0-255`          | Used to troubleshoot network issues                                                                                                                                                |
| Internet Group Management Protocol                        | `IGMP`       | `0-255`          | Used for multicasting                                                                                                                                                              |
| Oracle DB (Default/Alternative) Listener                  | `oracle-tns` | `1521`/`1526`    | The Oracle database default/alternative listener is a service that runs on the database host and receives requests from Oracle clients.                                            |
| Ingres Lock                                               | `ingreslock` | `1524`           | Ingres database is commonly used for large commercial applications and as a backdoor that can execute commands remotely via RPC.                                                   |
| Squid Web Proxy                                           | `http-proxy` | `3128`           | Squid web proxy is a caching and forwarding HTTP web proxy used to speed up a web server by caching repeated requests.                                                             |
| Secure Copy Protocol                                      | `SCP`        | `22`             | Securely copy files between systems                                                                                                                                                |
| Session Initiation Protocol                               | `SIP`        | `5060`           | Used for VoIP sessions                                                                                                                                                             |
| Simple Object Access Protocol                             | `SOAP`       | `80`, `443`      | Used for web services                                                                                                                                                              |
| Secure Socket Layer                                       | `SSL`        | `443`            | Securely transfer files                                                                                                                                                            |
| TCP Wrappers                                              | `TCPW`       | `113`            | Used for access control                                                                                                                                                            |
| Internet Security Association and Key Management Protocol | `ISAKMP`     | `500`            | Used for VPN connections                                                                                                                                                           |
| Microsoft SQL Server                                      | `ms-sql-s`   | `1433`           | Used for client connections to the Microsoft SQL Server.                                                                                                                           |
| Kerberized Internet Negotiation of Keys                   | `KINK`       | `892`            | Used for authentication and authorization                                                                                                                                          |
| Open Shortest Path First                                  | `OSPF`       | `89`             | Used for routing                                                                                                                                                                   |
| Point-to-Point Tunneling Protocol                         | `PPTP`       | `1723`           | Is used to create VPNs                                                                                                                                                             |
| Remote Execution                                          | `REXEC`      | `512`            | This protocol is used to execute commands on remote computers and send the output of commands back to the local computer.                                                          |
| Remote Login                                              | `RLOGIN`     | `513`            | This protocol starts an interactive shell session on a remote computer.                                                                                                            |
| X Window System                                           | `X11`        | `6000`           | It is a computer software system and network protocol that provides a graphical user interface (GUI) for networked computers.                                                      |
| Relational Database Management System                     | `DB2`        | `50000`          | RDBMS is designed to store, retrieve and manage data in a structured format for enterprise applications such as financial systems, customer relationship management (CRM) systems. |

## Tasks of TCP/IP

| **Task**               | **Protocol** | **Description**                                                                                                                                                                                                                                                                                                                        |
| ---------------------- | ------------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Logical Addressing`   | `IP`         | Due to many hosts in different networks, there is a need to structure the network topology and logical addressing. Within TCP/IP, IP takes over the logical addressing of networks and nodes. Data packets only reach the network where they are supposed to be. The methods to do so are `network classes`, `subnetting`, and `CIDR`. |
| `Routing`              | `IP`         | For each data packet, the next node is determined in each node on the way from the sender to the receiver. This way, a data packet is routed to its receiver, even if its location is unknown to the sender.                                                                                                                           |
| `Error & Control Flow` | `TCP`        | The sender and receiver are frequently in touch with each other via a virtual connection. Therefore control messages are sent continuously to check if the connection is still established.                                                                                                                                            |
| `Application Support`  | `TCP`        | TCP and UDP ports form a software abstraction to distinguish specific applications and their communication links.                                                                                                                                                                                                                      |
| `Name Resolution`      | `DNS`        | DNS provides name resolution through Fully Qualified Domain Names (FQDN) in IP addresses, enabling us to reach the desired host with the specified name on the internet.                                                                                                                                                               |

## 3 Way Handshake


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/net/sec/tools/nmap-full-open-scan/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

<div class="markdown-embed-title">

# Three Way Handshake

</div>



When two parties establish a connection using TCP, they perform a three-way handshake. A three-way handshake starts the connection and exchanges all the parameters needed for the two parties to communicate. TCP uses a three-way handshake to establish a new connection. Initially, the client-side connection is in the closed state and the server-side in the listening state. The client initiates the connection by sending the initial sequence number (ISN) and setting the SYN flag. The client is now in the SYN-SENT state. When the server receives this packet, it acknowledges the client sequence number and sends its own ISN with the SYN flag set. The server’s state is now SYN-RECEIVED. On receipt of this packet, the client acknowledges the server sequence number by incrementing it and setting the ACK flag. The client is now in the established state. At this point, the two machines have established a session and can communicate. On receiving the client’s acknowledgement, the server enters the established state and sends an acknowledgment, incrementing the client’s sequence number. The connection can be closed either by using the FIN or RST flag or through a time out. If the RST flag of a packet is set, the receiving host enters the CLOSED state and frees all resources associated with this connection. This leads to the connection drop of any additional incoming packets. If the packet is sent with the FIN flag turned on, the receiving host closes the connection because it enters the CLOSE-WAIT state. The packets sent by the client are accepted in an established connection if the sequence number is within the range and follows its predecessor. If the sequence number is beyond the range of the acceptable sequence numbers, it drops the packet and sends an ACK packet using the expected sequence number. 


![nmap - Full-Open Scan-1752690940365.webp|532x396](/img/user/nmap%20-%20Full-Open%20Scan-1752690940365.webp)

```bash
nmap -sT 192.168.64.5 > tcp.connect.txt
```

</div></div>
