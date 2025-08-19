---
{"dg-publish":true,"permalink":"/ffuf/"}
---

- [[ffuf - Flags\|ffuf - Flags]]

Alternative to [[net/sec/tools/gobuster\|gobuster]], [[dirb\|dirb]]

- https://github.com/ffuf/ffuf/wiki
- https://medium.com/quiknapp/fuzz-faster-with-ffuf-c18c031fc480


## ffuf examples

### Directory Enumeration

```bash
ffuf -ic -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u "http://83.136.248.27:44254/FUZZ"
```

```
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u "http://test.academy.htb:57617/FUZZ"
```

_:Fuzz is not necessary here_
```bash
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt -u "http://83.136.248.27:44254/FUZZ"
```
_Only match HTTP 200_
```bash
ffuf -c -w /usr/share/wordlists/seclists/Discovery/Web-Content/raft-medium-directories.txt -u "http://sea.htb/FUZZ" -t 200
```

### Extension fuzzing

```shell-session
ffuf -ic -w /usr/share/wordlists/seclists/Discovery/Web-Content/web-extensions.txt:FUZZ -u "http://83.136.248.27:44254/blog/indexFUZZ"
```

```
ffuf -ic -w /usr/share/wordlists/seclists/Discovery/Web-Content/web-extensions.txt:FUZZ -u "http://academy.htb:57617/indexFUZZ"
```

After confirming extension we can use `-e .php,phps,php7`
### Page fuzzing 

```bash
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u http://83.136.248.27:44254/blog/FUZZ.php
```

### [[Subdomain enumeration\|Subdomain Enumeration]] 

```bash
ffuf -ic -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u http://FUZZ.inlanefreight.com
```

### [[virtual host\|vhost]] fuzzing

Using `/usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt`

```bash
ffuf -ic -u http://linkvortex.htb/ -w /usr/share/amass/wordlists/subdomains-top1mil-5000.txt -H "Host:FUZZ.linkvortex.htb"  -mc 200
```

```bash
ffuf -ic -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u http://academy.htb:PORT/ -H 'Host: FUZZ.academy.htb'
```



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




```bash
-recursion -recursion-depth 1
```

- Using `/usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt`
- And `-recursion -recursion-depth 1` 


```bash
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u http://83.136.248.27:44254/FUZZ -recursion -recursion-depth 1 -e .php -v
```

```
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory-list-2.3-small.txt:FUZZ -u "http://faculty.academy.htb:31772/courses/FUZZ" -recursion -recursion-depth 1 -e .php,.php7,.phps
```

</div></div>


### Parameter fuzzing

#### [[net/protocols/Hypertext Transfer Protocol\|HTTP]] [[HTTP GET Method\|GET]]
```shell-session
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ -u http://admin.academy.htb:PORT/admin/admin.php?FUZZ=key 
```

```shell-session
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ -u http://faculty.academy.htb:31772/courses/linux-security.php7?FUZZ=key 
```
#### [[net/protocols/Hypertext Transfer Protocol\|HTTP]] [[HTTP POST Method\|POST]]

- To fuzz the `data` field with `ffuf`, we can use the `-d` flag
- We also have to add `-X POST` to send `POST` requests.

```shell-session
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ -u http://admin.academy.htb:44462/admin/admin.php -X POST -d 'FUZZ=key' -H 'Content-Type: application/x-www-form-urlencoded' 
```


```shell-session
ffuf -w /usr/share/wordlists/seclists/Discovery/Web-Content/burp-parameter-names.txt:FUZZ -u http://faculty.academy.htb:31772/courses/linux-security.php7 -X POST -d 'FUZZ=key' -H 'Content-Type: application/x-www-form-urlencoded' 
```
Then, use a ids.txt to find out key


```bash
ffuf -w ids.txt:FUZZ -u http://admin.academy.htb:44462/admin/admin.php -X POST -d 'id=FUZZ' -H 'Content-Type: application/x-www-form-urlencoded'
```
## Filter out size

Don't contain the specific size

`-fs`

```bash
ffuf -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u http://academy.htb:41028/ -H 'Host: FUZZ.academy.htb' -fs 986
```

## Custom Wordlist

```
ffuf -w ids.txt:FUZZ -u http://admin.academy.htb:44462/admin/admin.php -X POST -d 'id=FUZZ' -H 'Content-Type: application/x-www-form-urlencoded' 
```

---

```cardlink
url: https://github.com/ffuf/ffuf
title: "GitHub - ffuf/ffuf: Fast web fuzzer written in Go"
description: "Fast web fuzzer written in Go. Contribute to ffuf/ffuf development by creating an account on GitHub."
host: github.com
favicon: https://github.githubassets.com/favicons/favicon.svg
image: https://opengraph.githubassets.com/7311acf9b56695d19a8f89793365aed7445cd7ff072a66ccb9f947f9e6e63659/ffuf/ffuf
```


