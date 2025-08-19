---
{"dg-publish":true,"permalink":"/ldapsearch/"}
---

```bash
ldapsearch -x -LLL -H ldap://ipa.example.com -D "uid=admin,cn=users,cn=accounts,dc=example,dc=com" -W -b "uid=user1,cn=users,cn=accounts,dc=example,dc=com" uid
```


```bash
ldapsearch -H ldap://ldap.example.com:389 -D "cn=admin,dc=example,dc=com" -w secret123 -b "ou=people,dc=example,dc=com" "(mail=john.doe@example.com)"
```


## Flags


|     |                                |
| --- | ------------------------------ |
| -H  | Host                           |
| -D  | [[Distinguished Name\|DN]]     |
| -w  | password                       |
| -b  | Base[[Distinguished Name\|DN]] |
|     |                                |
