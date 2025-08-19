---
{"dg-publish":true,"permalink":"/kerberoasting/"}
---

**Kerberoasting** is a [[Privilege Escalation\|post-exploitation]] attack technique that targets the Kerberos authentication protocol, commonly used in Microsoft [[sysadmin/windows/Active Directory\|Active Directory]] environments. It allows attackers to extract and crack service account credentials, facilitating privilege escalation and lateral movement within the network.

### Methodology

1. **[[Service Principal Names\|Service Principal Names]] (SPN) Enumeration**
   An attacker identifies Active Directory accounts with associated SPNs. These SPNs correspond to service accounts that authenticate services like SQL Server or IIS.
2. **Requesting Service Tickets**
   Using tools like [[Rubeus\|Rubeus]] or [[GetUserSPNs.py\|GetUserSPNs.py]], the attacker requests [[Kerberos service tickets\|Kerberos service tickets]] (TGS) for the identified SPNs.
3. **Extracting and Cracking Tickets**
   The attacker extracts the service tickets and attempts to crack the encrypted password hashes offline using brute-force tools like Hashcat or John the Ripper.
4. **Gaining Unauthorized Access**
   Once the plaintext password is obtained, the attacker can authenticate as the service account, gaining access to resources and systems associated with that account.
   
- [[AS-REP Roasting\|AS-REP Roasting]]
- [[AS-REP Roasting vs Kerberoasting\|AS-REP Roasting vs Kerberoasting]]

## Tools 

[[Rubeus\|Rubeus]]