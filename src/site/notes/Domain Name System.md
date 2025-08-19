---
{"dg-publish":true,"permalink":"/domain-name-system/"}
---


## Concepts

| DNS Concept                        | Description                                                                      | Example                                                                                                                             |
| ---------------------------------- | -------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------- |
| Domain Name                        | A human-readable label for a website or other internet resource.                 | www.example.com                                                                                                                     |
| [[IP Address\|IP Address]]                     | A unique numerical identifier assigned to each device connected to the internet. | 192.0.2.1                                                                                                                           |
| DNS Resolver                       | A server that translates domain names into IP addresses.                         | Your ISP's DNS server or public resolvers like Google DNS (8.8.8.8)                                                                 |
| [[Root Name Server\|Root Name Server]]               | The top-level servers in the DNS hierarchy.                                      | There are 13 root servers worldwide, named A-M: a.root-servers.net                                                                  |
| [[TLD Name Server\|TLD Name Server]]                | Servers responsible for specific top-level domains (e.g., .com, .org).           | [Verisign](https://en.wikipedia.org/wiki/Verisign) for .com, [PIR](https://en.wikipedia.org/wiki/Public_Interest_Registry) for .org |
| [[Authoritative Name Server\|Authoritative Name Server]]      | The server that holds the actual IP address for a domain.                        | Often managed by hosting providers or domain registrars.                                                                            |
| [[DNS Records\|DNS Records Types]] | Different types of information stored in DNS.                                    | A, AAAA, CNAME, MX, NS, TXT, etc.                                                                                                   |
|                                    |                                                                                  |                                                                                                                                     |

- https://en.wikipedia.org/wiki/Domain_Name_System

**1.** **User Request:**

When you type a website address into your browser, your computer sends a request to a DNS server. 

**2.** **Local Cache Check:**

The DNS server first checks its own cache for the IP address associated with that domain name. If found, the IP address is returned, and the process is complete. 

**3.** **Recursive Resolver:**

If the IP address isn't in the cache, the DNS server (acting as a recursive resolver) queries other DNS servers to find the correct IP address. 

**4.** **Root Server:**

The recursive resolver starts by querying a root server, which directs it to the appropriate top-level domain (TLD) server (e.g., .com, .org). 

**5.** **TLD Server:**

The TLD server then directs the resolver to the authoritative nameserver for the specific domain. 

**6.** **Authoritative Server:**

The authoritative nameserver, which holds the definitive information for that domain, provides the IP address to the recursive resolver. 

**7.** **Return Journey:**
The recursive resolver then sends the IP address back to your computer, allowing it to connect to the website.

---

![|933x434](https://academy.hackthebox.com/storage/modules/289/DNS/DNS_Query_Process-2.png)

- [[DNS Troubleshooting\|DNS Troubleshooting]]
- [[DNS Caching\|DNS Caching]]

## Tools

- https://dnsdumpster.com
- [[resolvectl\|resolvectl]]

## ISP DNS Servers

- TCS Internet - `131.200.5.1`

[How to point a domain to Azure - Domains - Namecheap.com](https://www.namecheap.com/support/knowledgebase/article.aspx/9846/2208/how-to-point-a-domain-to-azure/)
[How to Really Map a Namecheap URL to Your Static Azure Cloud Website | by John Conley | Medium](https://medium.com/@bruvajc/how-to-really-map-a-namecheap-url-to-your-static-azure-cloud-website-3aa9d42dba26)

## CNAME records

### [About CNAME records - Google Workspace Admin Help](https://support.google.com/a/answer/112037?hl=en#zippy=%2Cset-up-cname-records-now)

A Canonical Name or CNAME record is a type of DNS record that maps an alias name to a true or *canonical* domain name.

## ecs vs dnssec

- https://www.reddit.com/r/pihole/comments/edsfy5/could_someone_explain_to_me_the_differences_of/

## fixing DNS in [[raspberry pi\|raspberry pi]]

https://www.jeffgeerling.com/blog/2024/resolving-temporary-failure-name-resolution-on-pi-os-12-bookworm

## Lookup tool

- [[sre/Tools/dig\|dig]]

## DNS Hierarchy

DNS is organized like a tree, starting from the root and branching out into different layers.

| **Layer**                  | **Description**                                                                   |
| -------------------------- | --------------------------------------------------------------------------------- |
| `Root Servers`             | The top of the DNS hierarchy.                                                     |
| `Top-Level Domains (TLDs)` | Such as `.com`, `.org`, `.net`, or country codes like `.uk`, `.de`.               |
| `Second-Level Domains`     | For example, `example` in `example.com`.                                          |
| `Subdomains or Hostname`   | For instance, `www` in `www.example.com`, or `accounts` in `accounts.google.com`. |

## DNS Resolution Process (Domain Translation)

When we enter a domain name in our browser, the computer needs to find the corresponding IP address. This process is known as `DNS resolution` or `domain translation`. The steps below show how this process works.

| **Step** | **Description**                                                                                                                                                  |
| -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `Step 1` | We type `www.example.com` into our browser.                                                                                                                      |
| `Step 2` | Our computer checks its local DNS cache (a small storage area) to see if it already knows the IP address.                                                        |
| `Step 3` | If not found locally, it queries a `recursive DNS server`. This is often provided by our Internet Service Provider or a third-party DNS service like Google DNS. |
| `Step 4` | The recursive DNS server contacts a `root server`, which points it to the appropriate `TLD name server` (such as the `.com` domains, for instance).              |
| `Step 5` | The TLD name server directs the query to the `authoritative name server` for `example.com`.                                                                      |
| `Step 6` | The authoritative name server responds with the IP address for `www.example.com`.                                                                                |
| `Step 7` | The recursive server returns this IP address to your computer, which can then connect to the website’s server directly.                                          |
