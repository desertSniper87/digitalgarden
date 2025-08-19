---
{"dg-publish":true,"permalink":"/subdomain-enumeration/"}
---



- https://www.ceeyu.io/resources/blog/subdomain-enumeration-tools-and-techniques
- https://blog.appsecco.com/a-penetration-testers-guide-to-sub-domain-enumeration-7d842d5570f6
- https://0xffsec.com/handbook/information-gathering/subdomain-enumeration/

## Tools

- [[FinalRecon\|FinalRecon]]
- [[netcraft\|netcraft]]
- [[dnsdumpster\|dnsdumpster]]
- [[subfinder\|subfinder]]
## [[net/sec/tools/Seclists\|Wordlist]]


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">



### [[Subdomain enumeration\|Subdomain enumeration]]

```
/usr/share/amass/wordlists/subdomains-top1mil-5000.txt
```

```
/usr/share/seclists/Discovery/DNS/namelist.txt
```

```
/usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt
```


</div></div>


## Using [[net/sec/amass\|amass]]

```bash
amass enum --passive -d $url
```

## Using [[fierce\|fierce]]

```bash
fierce --domain bcc.gov.bd
```

## Using [[ffuf\|ffuf]]



<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/ffuf/#subdomain-enumeration" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">



### [[Subdomain enumeration\|Subdomain Enumeration]] 

```bash
ffuf -ic -w /usr/share/wordlists/seclists/Discovery/DNS/subdomains-top1million-5000.txt:FUZZ -u http://FUZZ.inlanefreight.com
```


</div></div>


## Using [[dnsenum\|dnsenum]]


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/dnsenum/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




Comprehensive DNS enumeration tool that supports dictionary and brute-force attacks for discovering subdomains.

```bash
dnsenum --enum inlanefreight.com -f /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -r
```

</div></div>


## Using [[Google Dorks\|Google Dorks]]

```
site:bcc.gov.bd -domain:www
```

## Using [[dnsrecon\|dnsrecon]]


<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/dnsrecon/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">




A tool for deep DNS reconnaissance. **DNSRecon** helps enumerate DNS records like A, AAAA, and CNAME. It also supports zone transfers and NSEC-based enumerations to find hidden domains.

- [GitHub - darkoperator/dnsrecon: DNS Enumeration Script](https://github.com/darkoperator/dnsrecon)



```
dnsrecon -d inlanefreight.com
```

</div></div>



## Using [[sublist3r\|sublist3r]]


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




```
sublist3r -d eccouncil.org -o eccouncil_subdomains.txt 
```

</div></div>




---
- [[Zone transfer\|DNS zone transfer]]
- [[Certificate Transparency Logs\|Certificate Transparency Logs]] logs