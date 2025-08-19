---
{"dg-publish":true,"permalink":"/net/windows/server-message-block/"}
---

## References

- [Enumerating SMB, RPC, and NetBIOS for Pentesting (Ports 445, 135-139)](https://infinitelogins.com/2020/06/17/enumerating-smb-for-pentesting/)
## Ports

Initially, it was designed to run on top of [[Netbios\|NetBIOS]] over TCP/IP (NBT) using,
- [[net/protocols/Transmission Control Protocol\|TCP]] port `139` and [[User Datagram Protocol\|UDP]] ports `137` and `138`.
- However, with Windows 2000, Microsoft added the option to run SMB directly over TCP/IP on port `445` without the extra [[Netbios\|NetBIOS]] layer.

- Samba is a Unix/[[os/Linux\|Linux]]-based open-source implementation of the SMB protocol
## Tools

- [[net/windows/tools/smbclient\|smbclient]]
- [[enum4linux\|enum4linux]]
- [[smbmap\|smbmap]]

## [[net/sec/tools/nmap\|nmap]]

```shell-session
nmap 10.129.14.128 -sV -sC -p139,445
```

### OS Discovery

```shell-session
nmap --script smb-os-discovery.nse -p445 10.10.10.40
```


## Example

![image-1-27.webp](/img/user/image-1-27.webp)

- We can see that it performs the TCP handshake each time it establishes a session `orange boxes`
- When looking at the source and destination ports `blue box`
- If we look at the `green boxes,` the info field tells us a bit about what is happening in the SMB communication
	- there are many errors
## Exploits

- [[Remote Command Execution\|Remote Command Execution]]
- Extract Hashes from SAM Database
- Enumerating Logged-on Users
- [[Pass-the-Hash\|Pass-the-Hash]] (PTH)

| Exploit                                                                     | Version       |
| --------------------------------------------------------------------------- | ------------- |
| [Rapid7](https://www.rapid7.com/db/modules/exploit/linux/samba/trans2open/) | 2.2.0 - 2.2.8 |
