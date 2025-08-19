---
{"dg-publish":true,"permalink":"/ntlm/"}
---

- A suite of [[Microsoft\|Microsoft]] security [[Protocol\|Protocol]] for authenticating users and computers based on a challenge-response mechanism.
- The **client** sends a hashed [[net/sec/Password\|password]] to the **server**, which challenges the client to prove it knows the password without sending it over the network.
- Microsoft introduced the NT LAN Manager (NTLM) hash in 1993 with Windows NT 3.1. NTLM hashes use [[MD4\|MD4]] to hash passwords in [[UTF-16\|UTF-16]] Little Endian format, supporting longer and more complex passwords without the limitations of the [[LM Hash\|LM Hash]].
## NTLM V2

- User passwords are stored as NT hashes (MD4 hash of the Unicode password)
- NTLMv2 hash = HMAC-MD5(NT hash, uppercase(username) + domain)
- NTLMv2_response = temp + blob
	- temp = HMAC-MD5(NTLMv2_hash, server_challenge + blob) 


- Challenge Response Auth method
	- User sends a negotiation message
		- Domain Name
	- [[Domain Controller\|Domain Controller]] sends a challenge (Random Nonce)
	- Client Sends NTLMv2 Response
	- Server Verifies NTLMv2 response

![|364x218](https://i0.wp.com/lab.wallarm.com/wp-content/uploads/2023/10/The-NTLM-Process-min.jpg?w=770&ssl=1)


---
- [NTLM Explained: Definition, Protocols & More \| CrowdStrike](https://www.crowdstrike.com/en-us/cybersecurity-101/identity-protection/windows-ntlm/)
---
## Weakness

- [[MD4\|MD4]] has known collision attacks since 2004
- [[md5\|MD5]] has collision attacks and is considered insecure
- [[Pass-the-Hash\|Pass-the-Hash]] attacks
- [[Dictionary attack\|Dictionary Attack]]s
- [[Hash Relay attacks\|Hash Relay attacks]]

