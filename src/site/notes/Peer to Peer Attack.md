---
{"dg-publish":true,"permalink":"/peer-to-peer-attack/"}
---

A peer-to-peer attack is a form of DDoS attack in which the attacker exploits a number of bugs in peer-to-peer servers to initiate a DDoS attack
- Attackers exploit flaws found in networks that use the [[Direct Connect\|Direct Connect]] (DC++) protocol, which allows the exchange of files between instant-messaging clients
- This kind of attack does not use botnets
- Unlike a botnet-based attack, a peer-to-peer attack eliminates the need for attackers to communicate with the clients they subvert
- Here, the attacker instructs clients of large peer-to-peer file sharing hubs to disconnect from their peer-to-peer network and instead connect to the victim’s website
- Consequently, several thousand computers may aggressively attempt to connect to a target website, causing a drop in the performance of the target website
- It is easy to identify peer-to-peer attacks based on signatures
- By using this method, attackers launch massive DoS attacks to compromise websites.

Peer-to-peer DDoS attacks can be minimized by specifying ports for peer-to-peer communication
- For example, specifying port 80 to disallow peer-to-peer communication minimizes the possibility of attacks on websites.
