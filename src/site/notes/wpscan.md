---
{"dg-publish":true,"permalink":"/wpscan/"}
---


[WPScan](https://github.com/wpscanteam/wpscan) is an automated [[WordPress\|WordPress]] scanner and enumeration tool

```bash
wpscan -u james -P /password.txt — url http://172.16.0.27:8080/CEH/
```

```bash
wpscan --url 172.28.128.4/wordpress --wp-content-dir /wp-admin -e

```
```
wpscan --enumerate --url http://179.61.189.204 --api-token kGrndcbVUXVNPpHWoo8b8AnksQMMe2QN7vfxjMyZF7I
```

## Token

```
kGrndcbVUXVNPpHWoo8b8AnksQMMe2QN7vfxjMyZF7I
```

## Enumerate

```bash
wpscan --url http://94.237.55.43:56314 --enumerate
```

## [[Brute force\|Brute Force]] using [[xmlrpc\|xmlrpc]]

```bash
wpscan --password-attack xmlrpc -t 20 -U roger -P /usr/share/wordlists/rockyou.txt --url http://94.237.55.43:56314
```

```
wpscan --password-attack xmlrpc -t 20 -U admin -P /usr/share/wordlists/rockyou.txt --url http://94.237.55.43:56314
```

## Building from source

```bash
git clone https://github.com/wpscanteam/wpscan
```
```
cd wpscan/
```
```
# gem install bundler
```
```
gem build wpscan.gemspec
```
```
# bundle install --without test
```
```
gem install wpscan-3.8.28.gem
```
