---
{"dg-publish":true,"permalink":"/uniscan-tutorial/"}
---


## Tutorial
#chatgpt 

`uniscan` is a popular web vulnerability scanner that automates the detection of common vulnerabilities in web applications. It’s often used in security assessments to look for weak spots like SQL injections, XSS, and directory/file vulnerabilities. Here are some basic `uniscan` commands to get started:

### Basic Scan
Scan a single URL for common vulnerabilities:
```bash
uniscan -u http://example.com -qweds
```
Options:
- `-q`: Check for directories.
- `-w`: Check for files.
- `-e`: Check for errors.
- `-d`: Dynamic checks (XSS, SQL Injection, etc.).
- `-s`: Static checks (HTML comments, exposed JS files).

### Directory and File Brute Forcing
To brute-force common directories and files:
```bash
uniscan -u http://example.com -qwf
```

### Custom User Agent
To use a custom User-Agent string:
```bash
uniscan -u http://example.com -qweds -a "Mozilla/5.0 (Windows NT 10.0; Win64; x64)"
```

### SQL Injection and XSS Only
If you want to focus only on SQL Injection and XSS vulnerabilities:
```bash
uniscan -u http://example.com -ds
```

### Verbose Mode
For more detailed output:
```bash
uniscan -u http://example.com -qweds -v
```

### Save Output to a File
To save the results of the scan:
```bash
uniscan -u http://example.com -qweds -o output.txt
```

### Perform a Scan on Multiple URLs
You can use `uniscan` with a file containing multiple URLs:
```bash
uniscan -f urls.txt -qweds
```

These examples can help automate initial checks for common vulnerabilities but remember to use tools like this ethically and with permission if targeting external sites.