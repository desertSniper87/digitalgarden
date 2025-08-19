---
{"dg-publish":true,"permalink":"/firewall/"}
---

***Filters traffic between private and public networks.*** 

A firewall is a software-or hardware-based system located at the network gateway that protects the resources of a private network from unauthorized access by users on other networks. They are placed at the junction or gateway between two networks, usually a private network and a public network such as the Internet. Firewalls examine all the messages entering or leaving the intranet and block those that do not meet the specified security criteria. Firewalls may be concerned with the type of traffic or with the source or destination addresses and ports. They include a set of tools that monitor the flow of traffic between networks. A firewall placed at the network level and working closely with the router filters all the network packets to determine whether to forward them toward their destinations. Always install firewalls away from the rest of the network, so that none of the incoming requests can gain direct access to a private network resource. If appropriately configured, the firewall protects systems on one side of it from systems on the other side. 

- [[Firewall Architecture\|Firewall Architecture]]

## Types 

- [[Software Firewall\|Software Firewall]]
- [[Hardware Firewall\|Hardware Firewall]]


## Firewall Technologies

- **[[Packet Filtering Firewall\|Packet Filtering Firewall]]**
- **[[Circuit-Level Gateway Firewall\|Circuit-Level Gateway Firewall]]**
- **[[Application-Level Firewall\|Application-Level Firewall]]**
- **[[Stateful Multilayer Inspection Firewall\|Stateful Multilayer Inspection Firewall]]**
- **[[Application Proxy Concepts\|Application Proxy Concepts]]**
- **[[Network Address Translation\|Network Address Translation]]**
- **[[net/vpn/Virtual Private Network\|Virtual Private Network]]**

### OSI Layer and Firewall Technologies

The table below summarizes technologies operating at each OSI layer:


| **Firewall Technology**                                        | **Mapped OSI Layers**                                                                                                                 |
| -------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **Virtual Private Network ([[net/vpn/Virtual Private Network\|VPN]])** | [[OSI Layer 7\|Application Layer]], [[OSI Layer 3\|Network Layer]], [[OSI Layer 2\|Data Link Layer]], [[OSI Layer 1\|Physical Layer]] |
| **Application Proxies**                                        | [[OSI Layer 7\|Application Layer]], [[OSI Layer 5\|Session Layer]]                                                                    |
| **Circuit-Level Gateways**                                     | [[OSI Layer 5\|Session Layer]], [[OSI Layer 4\|Transport Layer]]                                                                      |
| **[[Packet Filtering Firewall\|Packet Filtering Firewall]]**                              | [[OSI Layer 3\|Network Layer]]                                                                                                        |
| **Network Address Translation (NAT)**                          | [[OSI Layer 3\|Network Layer]]                                                                                                        |
| **Stateful Multilayer Inspection**                             | [[OSI Layer 3\|Network Layer]], [[OSI Layer 4\|Transport Layer]]                                                                      |




