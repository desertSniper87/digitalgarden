---
{"dg-publish":true,"permalink":"/hashcat/"}
---

- https://hashcat.net/hashcat/
- https://www.freecodecamp.org/news/hacking-with-hashcat-a-practical-guide/
- [example\_hashes \[hashcat wiki\]](https://hashcat.net/wiki/doku.php?id=example_hashes)


```bash
hashcat -m 0 -a 0 hash.txt rockyou.txt
```

## Salt


```
hashcat -a 0 -m 120 test.hash /usr/share/rockyou.txt
```


## [[bcrypt\|bcrypt]]


```bash
hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt --status --show
```

## [[Kerberoasting\|Kerberoasting]]

```bash
hashcat -m 13100 --force -a 0 hash.txt /root/ADtools/rockyou.txt
```

- -m 13100: This specifies the hash type. 13100 corresponds to Kerberos 5 AS-REQ Pre-Auth etype 23 (RC4-HMAC), a specific format for Kerberos hashes.
- --force: This option forces Hashcat to ignore warnings and run even if there are compatibility issues. Use this with caution, as it might cause instability or incorrect results.
- -a 0: This specifies the attack mode. 0 stands for a straight attack, which is a simple dictionary attack where Hashcat tries each password in the dictionary as it is.
- hash.txt: is the input file containing the hashes to crack
- /root/ADtools/rockyou.txt: is the wordlist file used for the attack

## Hash Types


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">

<div class="markdown-embed-title">

# Hash Types

</div>



| **Algorithm** | **Hash**       |
| ------------- | -------------- |
| Salted MD5    | `$1---
{"dg-publish":true,"permalink":"/hashcat/"}
---

- https://hashcat.net/hashcat/
- https://www.freecodecamp.org/news/hacking-with-hashcat-a-practical-guide/
- [example\_hashes \[hashcat wiki\]](https://hashcat.net/wiki/doku.php?id=example_hashes)


```bash
hashcat -m 0 -a 0 hash.txt rockyou.txt
```

## Salt


```
hashcat -a 0 -m 120 test.hash /usr/share/rockyou.txt
```


## [[bcrypt\|bcrypt]]


```bash
hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt --status --show
```

## [[Kerberoasting\|Kerberoasting]]

```bash
hashcat -m 13100 --force -a 0 hash.txt /root/ADtools/rockyou.txt
```

- -m 13100: This specifies the hash type. 13100 corresponds to Kerberos 5 AS-REQ Pre-Auth etype 23 (RC4-HMAC), a specific format for Kerberos hashes.
- --force: This option forces Hashcat to ignore warnings and run even if there are compatibility issues. Use this with caution, as it might cause instability or incorrect results.
- -a 0: This specifies the attack mode. 0 stands for a straight attack, which is a simple dictionary attack where Hashcat tries each password in the dictionary as it is.
- hash.txt: is the input file containing the hashes to crack
- /root/ADtools/rockyou.txt: is the wordlist file used for the attack

## Hash Types

...       |
| SHA-256       | `$5---
{"dg-publish":true,"permalink":"/hashcat/"}
---

- https://hashcat.net/hashcat/
- https://www.freecodecamp.org/news/hacking-with-hashcat-a-practical-guide/
- [example\_hashes \[hashcat wiki\]](https://hashcat.net/wiki/doku.php?id=example_hashes)


```bash
hashcat -m 0 -a 0 hash.txt rockyou.txt
```

## Salt


```
hashcat -a 0 -m 120 test.hash /usr/share/rockyou.txt
```


## [[bcrypt\|bcrypt]]


```bash
hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt --status --show
```

## [[Kerberoasting\|Kerberoasting]]

```bash
hashcat -m 13100 --force -a 0 hash.txt /root/ADtools/rockyou.txt
```

- -m 13100: This specifies the hash type. 13100 corresponds to Kerberos 5 AS-REQ Pre-Auth etype 23 (RC4-HMAC), a specific format for Kerberos hashes.
- --force: This option forces Hashcat to ignore warnings and run even if there are compatibility issues. Use this with caution, as it might cause instability or incorrect results.
- -a 0: This specifies the attack mode. 0 stands for a straight attack, which is a simple dictionary attack where Hashcat tries each password in the dictionary as it is.
- hash.txt: is the input file containing the hashes to crack
- /root/ADtools/rockyou.txt: is the wordlist file used for the attack

## Hash Types

...       |
| SHA-512       | `$6---
{"dg-publish":true,"permalink":"/hashcat/"}
---

- https://hashcat.net/hashcat/
- https://www.freecodecamp.org/news/hacking-with-hashcat-a-practical-guide/
- [example\_hashes \[hashcat wiki\]](https://hashcat.net/wiki/doku.php?id=example_hashes)


```bash
hashcat -m 0 -a 0 hash.txt rockyou.txt
```

## Salt


```
hashcat -a 0 -m 120 test.hash /usr/share/rockyou.txt
```


## [[bcrypt\|bcrypt]]


```bash
hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt --status --show
```

## [[Kerberoasting\|Kerberoasting]]

```bash
hashcat -m 13100 --force -a 0 hash.txt /root/ADtools/rockyou.txt
```

- -m 13100: This specifies the hash type. 13100 corresponds to Kerberos 5 AS-REQ Pre-Auth etype 23 (RC4-HMAC), a specific format for Kerberos hashes.
- --force: This option forces Hashcat to ignore warnings and run even if there are compatibility issues. Use this with caution, as it might cause instability or incorrect results.
- -a 0: This specifies the attack mode. 0 stands for a straight attack, which is a simple dictionary attack where Hashcat tries each password in the dictionary as it is.
- hash.txt: is the input file containing the hashes to crack
- /root/ADtools/rockyou.txt: is the wordlist file used for the attack

## Hash Types

...       |
| BCrypt        | `$2a---
{"dg-publish":true,"permalink":"/hashcat/"}
---

- https://hashcat.net/hashcat/
- https://www.freecodecamp.org/news/hacking-with-hashcat-a-practical-guide/
- [example\_hashes \[hashcat wiki\]](https://hashcat.net/wiki/doku.php?id=example_hashes)


```bash
hashcat -m 0 -a 0 hash.txt rockyou.txt
```

## Salt


```
hashcat -a 0 -m 120 test.hash /usr/share/rockyou.txt
```


## [[bcrypt\|bcrypt]]


```bash
hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt --status --show
```

## [[Kerberoasting\|Kerberoasting]]

```bash
hashcat -m 13100 --force -a 0 hash.txt /root/ADtools/rockyou.txt
```

- -m 13100: This specifies the hash type. 13100 corresponds to Kerberos 5 AS-REQ Pre-Auth etype 23 (RC4-HMAC), a specific format for Kerberos hashes.
- --force: This option forces Hashcat to ignore warnings and run even if there are compatibility issues. Use this with caution, as it might cause instability or incorrect results.
- -a 0: This specifies the attack mode. 0 stands for a straight attack, which is a simple dictionary attack where Hashcat tries each password in the dictionary as it is.
- hash.txt: is the input file containing the hashes to crack
- /root/ADtools/rockyou.txt: is the wordlist file used for the attack

## Hash Types

...      |
| Scrypt        | `$7---
{"dg-publish":true,"permalink":"/hashcat/"}
---

- https://hashcat.net/hashcat/
- https://www.freecodecamp.org/news/hacking-with-hashcat-a-practical-guide/
- [example\_hashes \[hashcat wiki\]](https://hashcat.net/wiki/doku.php?id=example_hashes)


```bash
hashcat -m 0 -a 0 hash.txt rockyou.txt
```

## Salt


```
hashcat -a 0 -m 120 test.hash /usr/share/rockyou.txt
```


## [[bcrypt\|bcrypt]]


```bash
hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt --status --show
```

## [[Kerberoasting\|Kerberoasting]]

```bash
hashcat -m 13100 --force -a 0 hash.txt /root/ADtools/rockyou.txt
```

- -m 13100: This specifies the hash type. 13100 corresponds to Kerberos 5 AS-REQ Pre-Auth etype 23 (RC4-HMAC), a specific format for Kerberos hashes.
- --force: This option forces Hashcat to ignore warnings and run even if there are compatibility issues. Use this with caution, as it might cause instability or incorrect results.
- -a 0: This specifies the attack mode. 0 stands for a straight attack, which is a simple dictionary attack where Hashcat tries each password in the dictionary as it is.
- hash.txt: is the input file containing the hashes to crack
- /root/ADtools/rockyou.txt: is the wordlist file used for the attack

## Hash Types

...       |
| Argon2        | `$argon2i---
{"dg-publish":true,"permalink":"/hashcat/"}
---

- https://hashcat.net/hashcat/
- https://www.freecodecamp.org/news/hacking-with-hashcat-a-practical-guide/
- [example\_hashes \[hashcat wiki\]](https://hashcat.net/wiki/doku.php?id=example_hashes)


```bash
hashcat -m 0 -a 0 hash.txt rockyou.txt
```

## Salt


```
hashcat -a 0 -m 120 test.hash /usr/share/rockyou.txt
```


## [[bcrypt\|bcrypt]]


```bash
hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt --status --show
```

## [[Kerberoasting\|Kerberoasting]]

```bash
hashcat -m 13100 --force -a 0 hash.txt /root/ADtools/rockyou.txt
```

- -m 13100: This specifies the hash type. 13100 corresponds to Kerberos 5 AS-REQ Pre-Auth etype 23 (RC4-HMAC), a specific format for Kerberos hashes.
- --force: This option forces Hashcat to ignore warnings and run even if there are compatibility issues. Use this with caution, as it might cause instability or incorrect results.
- -a 0: This specifies the attack mode. 0 stands for a straight attack, which is a simple dictionary attack where Hashcat tries each password in the dictionary as it is.
- hash.txt: is the input file containing the hashes to crack
- /root/ADtools/rockyou.txt: is the wordlist file used for the attack

## Hash Types

... |
## Hash cracking

- [[hashcat\|hashcat]]
- [[md5#md5 rainbow table\|md5#md5 rainbow table]]

## Hash Algorithms

- [[md5\|md5]]
- [[net/sec/sha-1\|sha-1]]
- [[sha256\|sha256]]
- [[sha512\|sha512]]

## Detect Hash types

- [r/oscp - Reddit](https://www.reddit.com/r/oscp/comments/h00z7g/hash_type_identifying/)

- [[hashid\|hashid]]
- [magic](https://gchq.github.io/CyberChef/#recipe=Magic(3,false,false,''))
- [Hash Analyzer - TunnelsUP](https://www.tunnelsup.com/hash-analyzer)
- https://hashes.com/en/tools/hash_identifier
- https://decode.fr

### [[hashcat\|Hashcat]]

 - [example\_hashes \[hashcat wiki\]](https://hashcat.net/wiki/doku.php?id=example_hashes)

</div></div>
