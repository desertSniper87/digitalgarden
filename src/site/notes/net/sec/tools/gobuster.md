---
{"dg-publish":true,"permalink":"/net/sec/tools/gobuster/"}
---

- [Git](https://github.com/OJ/gobuster)
- https://www.freecodecamp.org/news/gobuster-tutorial-find-hidden-directories-sub-domains-and-s3-buckets/

## Prequisites 

- [[net/sec/tools/Seclists\|Wordlist]]
   

## Brute force uris

```bash
gobuster dir -u $url -w /usr/share/seclists/Discovery/Web-Content/raft-small-words.txt -s "200,204,301,302,307,401,403" -b ""
```

## SSL Expired Error

- https://github.com/OJ/gobuster/issues/129


## Excluding length

- https://github.com/OJ/gobuster/issues/277

## Subdomain Enumuration

```
gobuster dns -d alert.htb -w /usr/share/wordlists/dirb/common.txt
```

## [[virtual host\|vhosts]]

```
gobuster vhost -u http://web1337.inlanefreight.htb:52323 -w /usr/share/wordlists/dirb/common.txt --append-domain
```