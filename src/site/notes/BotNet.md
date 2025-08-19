---
{"dg-publish":true,"permalink":"/bot-net/"}
---

A **botnet** is a network of **compromised computers** or **devices** (referred to as “bots” or “zombies”) that are controlled remotely by an attacker, often without the knowledge of the device owners. The attacker can use these botnets to perform various malicious activities, such as distributed denial-of-service (DDoS) attacks, data theft, or sending spam emails.
## Using [[msfvenom\|msfvenom]] to create Botnet

## Example


Mike works for a company “**Fourth Rose Intl**.” as the sales manager
- He was sent to Las Vegas on a business trip to meet his clients
- After the successful completion of his meeting, Mike went back to his hotel room, connected to the hotel Wi-Fi network and attended his other scheduled online client meetings through his laptop
- After returning back to his office headquarters, Mike connects his laptop to the office Wi-Fi network and continues his work; however, he observes *that his laptop starts to behave strangely*
- It regularly slows down with blue screening from time-to-time and rebooting without any apparent reason
- He raised the issue with his system administrator
- Some days later, the system administrator in Mike’s company observed the same issue in various other computers in his organization
- ==Meanwhile, he has also observed that large amounts of unauthorized traffic from various IP addresses of “**Fourth Rose Intl**.” were directed toward organizational web server==
- Security division of the company analyzed the network traces and identified that Mike’s Laptop’s IP address has authorized and initiated other computers in the network to perform DDoS abuse over the organizational web server
- They further identified a malicious executable backdoor file on **Mike’s Laptop** that connects to a remote anonymous computer
- This remote computer is responsible for sending commands to Mike’s Laptop in order to initiate and execute DDoS attack over the organizational web server
- In this case, Mike’s laptop was part of the  _________?