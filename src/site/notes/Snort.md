---
{"dg-publish":true,"permalink":"/snort/"}
---


**Snort** is an open-source **[[Intrusion Detection System\|Intrusion Detection System]] (IDS)** and **[[Intrusion Detection System\|Intrusion Prevention System]] (IPS)**.
- It is widely used for real-time traffic analysis and packet logging on IP networks.
- Snort can detect various types of attacks, including [[Buffer Overflow Attacks\|Buffer Overflow Attacks]], stealth port scans, [[Common Gateway Interface\|CGI]] attacks, [[net/windows/Server Message Block\|SMB]] probes, and much more.
- It can perform protocol analysis and content searching/matching, and it is used to detect a variety of attacks and probes, such as buffer overflows, stealth port scans, [[Common Gateway Interface\|CGI]] attacks, [[net/windows/Server Message Block\|SMB]] probes, and OS fingerprinting attempts.

- [[Snort Rules\|Snort Rules]]

## Example Snort Rule

```
alert tcp $EXTERNAL_NET any -> $HOME_NET 80 (msg:"WEB-MISC Command injection attempt"; flow:to_server,established; content:"cmd="; nocase; sid:1000001;)
```

![Snort-1755340362622.webp](/img/user/Snort-1755340362622.webp)