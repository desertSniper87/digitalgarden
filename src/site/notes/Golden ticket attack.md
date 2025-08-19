---
{"dg-publish":true,"permalink":"/golden-ticket-attack/"}
---


- Golden Ticket Attack is a post-exploitation attack in [[sysadmin/windows/Active Directory\|Active Directory]] environments.
- A Golden Ticket lets an attacker impersonate any user (including Domain Admins) in an AD domain indefinitely, bypassing normal authentication.

## Methodology

1. Attacker gets KRBTGT hash:
   - KRBTGT is a special AD account responsible for issuing Kerberos Ticket Granting Tickets (TGTs).
   - Its password hash is the key to the kingdom.
   - Usually stolen via tools like Mimikatz after Domain Admin access.

2. Crafts fake TGTs:
   - Using the KRBTGT hash, the attacker forges a Kerberos TGT ("Golden Ticket").
   - Can set arbitrary user info, group memberships, and expiration.

3. Gets access to any resource:
   - The forged TGT is accepted by domain services as legit.
   - Attacker can now request service tickets and access domain resources as any user.

## Tools

### [[net/sec/mimikatz\|mimikatz]]

  ```shell
  kerberos::golden /user:Administrator /domain:corp.local /sid:S-1-5-21... /krbtgt:<hash> /id:500
  ```

- [[lsadump\|lsadump]] can be used to dump the KRBTGT hash via [[DCSync\|dcsync]] attack. Then the [[NTLM\|NT Lan Manager]] hash can be used for Golden Ticket attacks. 

```bash
lsadump::dcsync /domain:domain name /user:krbtgt
```

### Impacket

## Defenses

- Rotate the KRBTGT password twice if compromise suspected.
- Enable Advanced Auditing and look for anomalous TGT creation.
- Use Tiered Admin model: never log in to lower-trust systems with high-privilege accounts.
- Monitor TGT lifetime anomalies, abnormal group memberships, or unusual source IPs.

