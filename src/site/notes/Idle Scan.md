---
{"dg-publish":true,"permalink":"/idle-scan/"}
---

- [elhacker.info/Cursos/Advanced Ethical Hacking - Network and Web PenTesting/Part II - Network and Web PenTesting/1. Network Scanning%2C Network Establishment%2C Web Vulnerabilities Exploitation/5.1 Stealth\_Idle\_Scan.pdf?utm\_source=chatgpt.com](https://elhacker.info/Cursos/Advanced%20Ethical%20Hacking%20-%20Network%20and%20Web%20PenTesting/Part%20II%20-%20Network%20and%20Web%20PenTesting/1.%20Network%20Scanning%2C%20Network%20Establishment%2C%20Web%20Vulnerabilities%20Exploitation/5.1%20Stealth_Idle_Scan.pdf?utm_source=chatgpt.com)
- [How does idle scan work?](https://vipulchaskar.blogspot.com/2014/04/how-does-idle-scan-work.html?utm_source=chatgpt.com)


- The IDLE/IPID header scan is a [[net/protocols/Transmission Control Protocol\|TCP]] port scan method that can be used to send a ==spoofed source address== to a computer to **determine what services are available**
- It offers the **complete blind scanning** of a remote host
- One way to determine whether a port is open is to send a “[[TCP SYN Flag\|SYN]]” (**session establishment**) packet to the port
- The target machine returns a “SYN|ACK” (**session request acknowledgement**) packet if the port is open or an “**RST**” (reset) packet if the port is closed
- A machine that receives an **==unsolicited SYN|ACK packet responds with an RST==**
- An **==unsolicited RST is ignored==**
- Every IP packet on the Internet has an “**IP identifier**” (**IPID**) that uniquely identifies **fragments** of an original IP datagram
- The **OS increases the IPID for each packet sent**
- Probing an IPID reveals to an attacker ==the number of packets sent== since the last probe
- The **-sI** option is used to perform an IDLE scan.
- The **attacker performs this scan by impersonating another computer via spoofing**
	- The attacker uses another host called a “zombie,” to scan the remote host and identify open ports
	- the attacker expects the sequence numbers of the zombie host
- If the remote host checks the IP of the scanning party
	- the IP of the zombie machine is displayed

## Step 1

- The first step in an idle scan is to determine an **appropriate zombie**
	- A zombie that **incrementally assigns IPID packets** on a **global basis** 
	- Idle zombie for performing idle scans
- The shorter the time interval for request/response between the attacker-zombie and zombie-target, the faster is the scan

- Choose a “Zombie” and Probe Its **Current IP Identification (IPID) Number In the first step**
- the **SYN+ACK** packet is sent to the zombie machine to probe its IPID number
	- the SYN+ACK packet is not sent to establish a TCP connection (three-way handshake).

- As the zombie does not expect a SYN+ACK packet
	- it denies the connection by returning an RST packet
	- The RST packet sent by the zombie machine is **analyzed to extract the IPID**

![Idle Scan-1752843750504.webp](/img/user/Idle%20Scan-1752843750504.webp)

## Step 2

- The attacker sends a SYN packet to the **target machine** on port 80
	- spoofing the IP address of the zombie

### If the port is open

- The target(server) sends the **SYN+ACK** packet to the **zombie** (as the IP address was spoofed) to proceed with the three-way handshake
- ==Because the zombie did not expect a SYN+ACK packet from the target machine==
	- it responds with an RST packet.

![Idle Scan-1752843761945.webp](/img/user/Idle%20Scan-1752843761945.webp)


- Every IP packet has an IPID, which increases by one for every packet transmission
- The zombie now uses the next available IPID

### If the port is closed

- Upon receiving the SYN packet from the attacker
	- the target responds with an RST packet
	- the zombie remains idle thereafter.

![Idle Scan-1752843781358.webp](/img/user/Idle%20Scan-1752843781358.webp)

- Attacker sends a SYN+ACK packet to the zombie
	- Zombie responds with an RST packet containing the IPID
- Assuming that the port on the target was open and that the zombie has already sent an RST packet to the target
	- the IPID number is increased by 1
- Now, the zombie responds with an RST packet to the attacker using its next IPID
	- the IPID is increased by 2
	- It implies that the port on the target machine was open


# [[net/sec/tools/nmap\|nmap]]


```
nmap -Pn -p 80 -sI 10.10.10.20 10.10.10.30
```