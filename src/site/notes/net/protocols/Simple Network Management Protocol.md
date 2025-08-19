---
{"dg-publish":true,"permalink":"/net/protocols/simple-network-management-protocol/"}
---

https://en.wikipedia.org/wiki/Simple_Network_Management_Protocol

- **SNMP Community strings** provide **information** and **statistics** about a [[Routers\|Router]] or device, helping us gain access to it
- The manufacturer default community strings of `public` and `private` are often unchanged
- In SNMP versions 1 and 2c, access is controlled using a plaintext community string, and if we know the name, we can gain access to it
- Encryption and authentication were only added in SNMP version 3
- Much information can be gained from SNMP
- Examination of process parameters might reveal credentials passed on the command line, which might be possible to reuse for other externally accessible services given the prevalence of password reuse in enterprise environments
- Routing information, services bound to additional interfaces, and the version of installed software can also be revealed.
## Tools

- [[snmpwalk\|snmpwalk]]
- [[onesixone\|onesixone]]


## Brute Forcing with [[net/sec/hydra\|hydra]]

```bash
hydra -P password-file.txt -v $ip snmp
```


## SNMP v1

- https://www.ibm.com/docs/en/aix/7.2?topic=management-snmpv1
- https://www.paessler.com/it-explained/what-is-an-snmp-community-string