---
{"dg-publish":true,"permalink":"/net/windows/tools/smbclient/"}
---

- [Linux Smbclient Command](https://www.computerhope.com/unix/smbclien.htm)
- ftp-like client to access SMB/CIFS resources on servers
- Note: If there is $ in resource it is default


- [Manfile](https://www.samba.org/samba/docs/current/man-html/smbclient.1.html)

- [Linux smbclient Command with Practical Examples \| LabEx](https://labex.io/tutorials/linux-linux-smbclient-command-with-practical-examples-422922)

## Example Commands


_List all resources without any password_
```
smbclient -L //10.10.159.242 -N
```

After you get the list, you connect the the share

```
smbclient //10.10.159.242 -N
```


```bash
smbclient //10.10.44.203/Anonymous -N
```

_Access SMB Share secret using the user suit_

```
smbclient //10.10.10.2/secret -U suit -p 445   #port 445 is optional
```

## Flags


|     |           |     |
| --- | --------- | --- |
| -L  | --list    |     |
| -N  | --no-pass |     |


### -L|--list

This option allows you to look at what services are available on a server. You use it as `smbclient -L` host and a list should appear. The -I option may be useful if your NetBIOS names don´t match your TCP/IP DNS host names or if you are trying to reach a host on another network.

## -N|--no-pass

If specified, this parameter suppresses the normal password prompt from the client to the user. This is useful when accessing a service that does not require a password.

Unless a password is specified on the command line or this parameter is specified, the client will
request a password.

If a password is specified on the command line and this option is also defined the password on the command line will be silently ignored and no password will be used.


## Commands

### mget \<mask\>

Copy all files matching `mask` from the server to the machine running the client.

Note that _`mask`_ is interpreted differently during recursive operation and non-recursive operation - refer to the recurse and mask commands for more information. Note that all transfers in `smbclient` are binary. See also the lowercase command.


List all share options
