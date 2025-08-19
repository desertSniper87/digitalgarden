---
{"dg-publish":true,"permalink":"/ids-evasion-attack/"}
---


An “evasion” attack occurs when the IDS discards packets while the host that has to get the packets accepts them.
- Using this technique, an attacker exploits the host computer.
- An evasion attack at the IP layer allows an attacker to attempt arbitrary attacks against hosts on a network without the IDS ever realizing it.
- ==The attacker sends portions of the request in packets that the IDS mistakenly rejects, allowing the removal of parts of the stream from the ID system's view==.
- For example, **if the attacker sends a malicious sequence byte by byte, and if the IDS rejects only one byte, it cannot detect the attack**.
- Here, the IDS gets fewer packets than the destination.

One example of an evasion attack is when an attacker opens a TCP connection with a data packet.
- Before any TCP connection can be used, it must be “opened” with a handshake between the two endpoints of the connection.
- An essential fact about TCP is that the handshake packets can themselves bear data.
- The IDS that does not accept the data in these packets is vulnerable to an evasion attack.

![IDS Evasion Attack-1755369471992.webp|901x389](/img/user/IDS%20Evasion%20Attack-1755369471992.webp)