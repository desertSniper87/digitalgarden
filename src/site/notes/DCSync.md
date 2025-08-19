---
{"dg-publish":true,"permalink":"/dc-sync/"}
---

A DCSync attack is a sophisticated technique where an attacker **impersonates** a [[Domain Controller\|Domain Controller]] (DC) to extract sensitive information from [[sysadmin/windows/Active Directory\|Active Directory]] (AD). By exploiting the Directory Replication Service Remote Protocol ([[MS-DRSR\|MS-DRSR]]), the attacker can request replication data from another DC, including password hashes and Kerberos keys, without directly accessing the target machine’s memory.

- [DCSync Ransomware Technique: Cybersecurity Definition \| Halcyon.ai](https://www.halcyon.ai/faqs/what-is-dcsync?utm_source=chatgpt.com)
- [Defending Your Directory: An Expert Guide to Securing Active Directory Against DCSync Attacks \| NCC Group](https://www.nccgroup.com/us/research-blog/defending-your-directory-an-expert-guide-to-securing-active-directory-against-dcsync-attacks/?utm_source=chatgpt.com)

## Retrieving password hashes of other domains

A domain controller (DC) in a Windows environment is configured to securely validate user requests within a domain. The function of a DC is to stockpile user accounts and data, provide authentication, and append a security policy for the domain. Replicating a directory in the IT environment plays a vital role as it assists system administrators to organize and handle data flow across many DCs. For example, when an employee of an organization updates their account credentials, the updated credentials should be replicated across all the DCs, which can facilitate easy authentication for users.

The DCSync attack is a technique used by attackers on selective DCs. In this attack, an attacker initially compromises and obtains privileged account access with domain replication rights. Then, they activate replication protocols to create a virtual DC similar to the original AD. This access enables the attacker to send requests to the DC and receive the victim’s confidential information such as NTLM password hashes. Using this information, an attacker can launch further attacks such as golden ticket attacks, account manipulation, and living off the land (LOTL) attacks as well as embed ransomware in the compromised servers.

## Methodology

![DCSync-1753987790612.webp|712x248](/img/user/DCSync-1753987790612.webp)

- Stage 1: Performs external [[Information Gathering\|Reconnaissance]] 
- Stage 2: Compromises the targeted machine 
- Stage 3: Performs internal reconnaissance 
- Stage 4: [[Privilege Escalation\|Escalates local privileges]] 
- Stage 5: Compromises credentials by sending commands to [[Domain Controller\|Domain Controller]] 
- Stage 6: Performs admin-level reconnaissance 
- Stage 7: Performs malicious [[Remote Code Execution\|Remote Code Execution]] 
- Stage 8: Gains domain admin credentials


