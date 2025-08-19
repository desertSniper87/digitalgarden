---
{"dg-publish":true,"permalink":"/denial-of-service/"}
---

- [[DoS Countermeasure Strategies\|DoS Countermeasure Strategies]]
## Techniques / Vectors

### [[OSI Layer 7\|Application Layer]] Attack Techniques
 
 Consume application resources or services, thereby making them unavailable to other legitimate users
 
- [[HTTP GET POST attack\|HTTP GET POST attack]]
- [[Slow Loris\|Slow Loris]] attack
- UDP application layer flood attack
- DDoS extortion attack

## Protocol Attack Techniques

Consume resources like connection state tables present in the network infrastructure components such as load-balancers, firewalls, and application servers

- [[Fragmentation Attack\|Fragmentation Attack]]
- [[Spoofed Session Flood Attack\|Spoofed Session Flood Attack]]
- [[TCP SYN Flag\|SYN]] flood attack
- [[TCP ACK FLAG\|ACK]] flood attack

## Volumetric Attack Techniques

Consume the bandwidth of the target network or service

- [[Ping of Death\|Ping of Death]]
- [[User Datagram Protocol\|UDP]] flood attack
- [[Ping\|ICMP]] [[ICMP Flood Attack\|Flood Attack]]
- [[Smurf Attack\|Smurf Attack]]
- [[Pulse wave attack\|Pulse wave]] and zero-day attack

---
- Compromise [[Availability\|Availability]]
	- Reduce
	- Restrict
	- Prevent 

## Tools

```
use auxiliary/dos/tcp/synflood
```


- [[I'm So Bored\|I'm So Bored]]
▪ High Orbit Ion Cannon (HOIC) (https://sourceforge.net) ▪ Low Orbit Ion Cannon (LOIC) (https://sourceforge.net) ▪ HULK (https://github.com) ▪ Slowloris (https://github.com) ▪ UFONet (https://ufonet.03c8.net) ▪ Packet Flooder Tool (https://www.netscantools.com)



### [[Distributed Denial of Service\|DDOS]]

- [[UltraDDOS-v2\|UltraDDOS-v2]]





## Example

Robert, a professional hacker, has launched a [[reflection attack\|reflection attack]] on the target organization’s Microsoft [[Cloud/vendors/azure/azure\|Azure]] environment to downgrade its network capacity
- For this purpose, he initiated sending a large number of spoofed [[User Datagram Protocol\|UDP]] packets with fake IP addresses that resembled the source IP addresses to an intermediary server
- The intermediary server started responding to all the source IP addresses at once causing legitimate users to wait for some time to receive the resources.