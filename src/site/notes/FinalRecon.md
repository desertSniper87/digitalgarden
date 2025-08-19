---
{"dg-publish":true,"permalink":"/final-recon/"}
---


[GitHub - thewhiteh4t/FinalRecon: All In One Web Recon](https://github.com/thewhiteh4t/FinalRecon)


```shell-session
git clone https://github.com/thewhiteh4t/FinalRecon.git
cd FinalRecon
pip3 install -r requirements.txt
chmod +x ./finalrecon.py
```

```shell-session
./finalrecon.py --headers --whois --url http://inlanefreight.com
```

```
./finalrecon.py --url http://web1337.inlanefreight.htb:52323/admin_h1dd3n --dir -w /usr/share/wordlists/seclists/Discovery/Web-Content/directory
-list-2.3-small.txt
```
## Flags

| Option         | Argument | Description                                         |
| -------------- | -------- | --------------------------------------------------- |
| `-h`, `--help` |          | Show the help message and exit.                     |
| `--url`        | URL      | Specify the target URL.                             |
| `--headers`    |          | Retrieve header information for the target URL.     |
| `--sslinfo`    |          | Get SSL certificate information for the target URL. |
| `--whois`      |          | Perform a Whois lookup for the target domain.       |
| `--crawl`      |          | Crawl the target website.                           |
| `--dns`        |          | Perform DNS enumeration on the target domain.       |
| `--sub`        |          | Enumerate subdomains for the target domain.         |
| `--dir`        |          | Search for directories on the target website.       |
| `--wayback`    |          | Retrieve Wayback URLs for the target.               |
| `--ps`         |          | Perform a fast port scan on the target.             |
| `--full`       |          | Perform a full reconnaissance scan on the target.   |