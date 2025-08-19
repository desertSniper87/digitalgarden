---
{"dg-publish":true,"permalink":"/as-rep-roasting/"}
---


AS-REP Roasting is a technique that enables adversaries to steal the password hashes of user accounts that have [[Kerberos preauthentication\|Kerberos preauthentication]] disabled, which they can then attempt to crack offline.

- An AS-REP roasting attack targets user accounts in AD
	- exploiting the DONT_REQ_PREAUTH setting
	- **Attackers** can request a ticket-granting ticket ([[Ticket Granting Ticket\|TGT]]) for these accounts *without needing the user's password*.

- The DC responds with an encrypted TGT
	- which the attacker captures
- This TGT is encrypted with the user's password hash
- TGT is subjected to offline password-cracking tools such as Hashcat or John the Ripper
- the attacker can eventually decrypt the TGT revealing the user's password.

## Get [[sysadmin/windows/Active Directory\|AD]] User information

```bash
python3 GetNPUsers.py CEH.com/ -no-pass -usersfile /root/ADtools/users.txt -dc-ip 10.10.1.22.
```

`no-pass`: Accounts not requiring [[Kerberos preauthentication\|Kerberos preauthentication]] flag
