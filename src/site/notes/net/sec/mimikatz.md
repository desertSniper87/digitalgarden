---
{"dg-publish":true,"permalink":"/net/sec/mimikatz/"}
---

Mimikatz is a command-line tool that allows attackers to obtain credentials from registry memory locations. 


- [GitHub - gentilkiwi/mimikatz: A little tool to play with Windows security](https://github.com/gentilkiwi/mimikatz)

## [[DCSync\|DCSync]]

Attackers leverage mimikatz to perform DCSync attacks. Mimikatz includes a DCSync command that utilizes the Microsoft Directory Replication Service Remote Protocol ([[MS-DRSR\|MS-DRSR]]) to replicate the behavior of a legitimate DC. Attackers execute the following command to retrieve the [[NTLM\|NTLM]] password hashes of an administrator account: 

```
mimikatz “lsadump::dcsync /domain:(domain name) /user:Administrator”
```
