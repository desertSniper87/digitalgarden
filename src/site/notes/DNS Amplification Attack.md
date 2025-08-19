---
{"dg-publish":true,"permalink":"/dns-amplification-attack/"}
---



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




- Step 1: Users who desire to resolve a domain name to its corresponding IP address send a DNS query to the primary DNS server specified in its Transmission Control Protocol ([[net/protocols/Transmission Control Protocol\|TCP]])/IP properties.
- Steps 2 to 7: If the requested DNS mapping does not exist on the user’s primary DNS server, the server forwards the request to the [[Root Name Server\|root server]]. The root server forwards the request to the .com namespace([[TLD Name Server\|TLD Name Server]]), where the user can find DNS mappings. This process repeats recursively until the DNS mapping is resolved.
- Step 8: Ultimately, when the system finds the primary DNS server for the requested DNS mapping, it generates a cache for the IP address in the user’s primary DNS server.



![dns - recursive query.webp|700x306](/img/user/dns%20-%20recursive%20query.webp)



</div></div>


Attackers exploit recursive DNS queries to perform a DNS amplification attack that results in DDoS attacks on the victim’s DNS server.

- Step 1: The attacker instructs compromised hosts ([[BotNet\|bots]]) to make DNS queries in the network.
- Step 2: All the compromised hosts spoof the victim’s IP address and send DNS query requests to the primary DNS server configured in the victim’s TCP/IP settings.
- Steps 3 to 8: If the requested DNS mapping does not exist on the victim’s primary DNS server, the server forwards the requests to the root server. The root server forwards the request to the .com or respective top-level domain (TLD) namespaces. This process repeats recursively until the victim’s primary DNS server resolves the DNS mapping request.
- Step 9: After the primary DNS server finds the DNS mapping for the victim’s request, it sends a DNS mapping response to the victim’s IP address. This response goes to the victim because bots use the victim’s IP address. The replies to copious DNS mapping requests from the bots result in DDoS on the victim’s DNS server.

![image-1-52.webp|1034x414](/img/user/image-1-52.webp)