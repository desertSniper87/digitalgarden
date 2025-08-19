---
{"dg-publish":true,"permalink":"/footprinting-example-script/"}
---


Using [[sre/Tools/dig\|dig]], [[whois\|whois]], [[net/sec/tools/theharvester\|theharvester]]

```python
import subprocess

def dns_lookup(domain):
    return subprocess.getoutput(f"dig {domain} ANY +noall +answer")
	
def whois_lookup(domain):
    return subprocess.getoutput(f"whois {domain}")
	
def email_enumeration(domain):
    return subprocess.getoutput(f"theHarvester -d {domain} -b all -l 100")
	
def run_footprinting(domain):
    print("Performing DNS Lookup...")
    dns_info = dns_lookup(domain)
    print(dns_info)

    print("\nPerforming Whois Lookup...")
    whois_info = whois_lookup(domain)
    print(whois_info)

    print("\nEnumerating Emails...")
    emails = email_enumeration(domain)
    print(emails)
	
```

```python
domain = 'www.microsoft.com'
run_footprinting(domain)
```