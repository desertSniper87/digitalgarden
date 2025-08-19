---
{"dg-publish":true,"permalink":"/snmpwalk/"}
---

- https://ezfive.com/snmpsoft-tools/snmp-walk/

```bash
snmpwalk -v 2c -c public underpass.htb
```

```shell-session
snmpwalk -v 2c -c public 10.129.42.253 1.3.6.1.2.1.1.5.0
```

```shell-session
snmpwalk -v 2c -c private  10.129.42.253 
```