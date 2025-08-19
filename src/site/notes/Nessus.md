---
{"dg-publish":true,"permalink":"/nessus/"}
---

- [Download](https://www.tenable.com/products/nessus/nessus-essentials)
- [tenable-prod](https://login.tenable.com/login)

## Removing Nessus

### [[apple/mac\|macos]]

```
rm -rf /Library/Nessus
rm -rf /Library/LaunchDaemons/com.tenablesecurity.nessusd.plist  
rm -rf /Library/PreferencePanes/Nessus Preferences.prefPane  
rm -rf /Applications/Nessus
```
## Cred

torsho/admin123
## Port

```
8834
```

## After Install


```
sudo systemctl status nessusd.service
sudo systemctl start nessusd.service
```

## chpasswd

```bash
/Library/Nessus/run/sbin/nessuscli chpasswd torsho
```
## Alternative

- [[Qualys\|Qualys]]
- [[openvas\|OpenVAS]]
- [[Acunetix\|Acunetix]]

## Plugins

- [[Terrascan\|Terrascan]]
- [[PCI-DSS\|PCI-DSS]]
	- [PCI-DSS Plugins For Nessus](https://www.tenable.com/blog/pci-dss-plugins-for-nessus)


## [[Windows\|Windows]]

```
net start "Tenable Nessus"
```
```
net stop "Tenable Nessus"
```


## Scheduling

## Report