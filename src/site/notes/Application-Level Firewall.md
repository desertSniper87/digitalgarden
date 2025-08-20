---
{"dg-publish":true,"permalink":"/application-level-firewall/"}
---


Application-based proxy firewalls focus on the **application layer** rather than just the packets.
- **Application-level gateways (proxies)** can filter packets at the **application layer** of the OSI model (or the application layer of TCP/IP).
- Incoming and outgoing traffic is restricted to services supported by the proxy; all other service requests are denied.
- The need for an application-level firewall arises from the tremendous amount of voice, video, and collaborative traffic in the data-link layer and network layer, which may be used for unauthorized access to internal and external networks.

Application-level gateways configured as web proxies prohibit FTP, gopher, telnet, or other traffic.
- They examine traffic and filter application-specific commands such as **HTTP: POST** and **GET**.
- Traditional firewalls are unable to filter such types of traffic.
- They can inspect, find, and verify malicious traffic that is missed by stateful inspection firewalls to make decisions as to whether to allow access, and they improve the overall security of the application layer.

For example, [[Worm\|Worms]] that send malicious code in legitimate protocols cannot be detected by **[[stateful firewalls\|stateful firewalls]]**, as proxy firewalls focus on packet headers in the network layer.
- However, **deep packet inspection firewalls** can find such attacks with the help of informative signatures added inside packets.

## Features of Application-Level Firewalls
- Analyze the application information to make decisions as to whether to permit traffic.
- Being proxy-based, they can permit or deny traffic according to the authenticity of the user or process involved.
- A **content-caching proxy** optimizes performance by caching frequently accessed information rather than sending new requests to the servers for the same old data.

## Modes of Application-Level Firewalls:

- **==Active Application-Level Firewalls==**: Examine all incoming requests, including the actual message that is exchanged, against known vulnerabilities such as SQL injection, parameter and cookie tampering, and cross-site scripting.
	- The requests that are deemed genuine are allowed to pass through them.
- **==Passive Application-Level Firewalls==**: Work similarly to **[[Intrusion Detection System\|IDS]]** in that they also check all incoming requests against known vulnerabilities, but they do not actively reject or deny those requests if a potential attack is discovered.

![Example of Application-Level Firewall](path-to-image)

