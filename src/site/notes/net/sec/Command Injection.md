---
{"dg-publish":true,"permalink":"/net/sec/command-injection/"}
---


- [Command Injection \| OWASP Foundation](https://owasp.org/www-community/attacks/Command_Injection)
- [Title Unavailable \| Site Unreachable](https://portswigger.net/web-security/os-command-injection)
- [Back to Basics: OS Command Injection \| Fastly](https://www.fastly.com/blog/back-to-basics-os-command-injection)
- [[net/sec/Command Injection - Cheatsheet\|Command Injection - Cheatsheet]]

## Tools

- [[sre/Tools/bash/Bashfuscator\|Bashfuscator]]
- [[Dosfuscation\|Dosfuscation]]

## Command Injection Characters


| **Injection Operator** | **Injection Character** | **URL-Encoded Character** | **Executed Command**                       |
| ---------------------- | ----------------------- | ------------------------- | ------------------------------------------ |
| **Semicolon**          | `;`                     | `%3b`                     | Both                                       |
| **New Line**           | `\n`                    | `%0a`                     | Both                                       |
| **Background**         | `&`                     | `%26`                     | Both (second output generally shown first) |
| Pipe                   | `\|`                    | `%7c`                     | Both **(only second output is shown**)     |
| AND                    | `&&`                    | `%26%26`                  | Both (only if first succeeds)              |
| OR                     | `\|\|`                  | `%7c%7c`                  | Second (only if first fails)               |
| Sub-Shell              | ` `` `                  | `%60%60`                  | Both (Linux-only)                          |
| Sub-Shell              | `$()`                   | `%24%28%29`               | Both (Linux-only)                          |
- `${IFS}` is space
- `${LS_COLORS:10:1}` is ;
- `${PATH:0:1}` is \

See also, 
<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




- [URL Decoder/Encoder](https://meyerweb.com/eric/tools/dencoder/)
- [CyberChef](https://cyberchef.io/#recipe=URL_Encode(false))
- [W3Schools.com](https://www.w3schools.com/tags/ref_urlencode.ASP)

> Characters beyond ASCII (such as €, •, and smart quotes) have different representations in Windows-1252 but are often encoded differently in UTF-8.
## Table

| Character | From [[Windows-1252\|Windows-1252]] | From [[UTF-8\|UTF-8]] |
| --------- | --------------------- | -------------- |
| space     | %20                   | %20            |
| !         | %21                   | %21            |
| "         | %22                   | %22            |
| #         | %23                   | %23            |
| '         | %27                   | %27            |
| "         | %22                   | %22            |
| #         | %23                   | %23            |
| ;         | %3B                   | %3B            |
| )         | %29                   | %29            |
| .         | %2E                   | %2E            |


</div></div>

## Payloads

- [Payloadbox​​](https://github.com/payloadbox/command-injection-payload-list)
- [GitHub - omurugur/OS\_Command\_Payload\_List: OS Command Injection Vulnerability Payload List](https://github.com/omurugur/OS_Command_Payload_List)



## [[Path traversal\|Path traversal]] 

[VulnLab—Path Traversal](https://medium.com/@mwar8205/vulnlab-path-traversal-14974774e2d4)

## Examples

```bash
127.0.0.1%0a{ls,-la}
```

```bash
127.0.0.1%0Als$%7BIFS%7D-la
```

```shell-session
$(rev<<<'imaohw')
```