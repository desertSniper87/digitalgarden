---
{"dg-publish":true,"permalink":"/sre/firewall/firewall-cmd/"}
---


## List all commands

```bash
firewall-cmd --list-all
```

## Add ports
```bash
firewall-cmd --permanent --add-port={80/tcp,443/tcp,389/tcp,636/tcp,88/tcp,464/tcp,53/tcp,88/udp,464/udp,53/udp,123/udp}
```

```bash
firewall-cmd --permanent --add-port={8774/tcp,8777/tcp,8778/tcp,8779/tcp}
```


## Reload

```bash 
sudo firewall-cmd --reload
```