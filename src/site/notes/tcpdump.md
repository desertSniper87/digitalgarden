---
{"dg-publish":true,"permalink":"/tcpdump/"}
---

- [[tcpdump - monitoring network traffic\|tcpdump - monitoring network traffic]]

- [[tcpdump - flags\|tcpdump - flags]]
- [[tcpdump - output\|tcpdump - output]]
- [[tcpdump - sudo exploit\|tcpdump - sudo exploit]]
- [[tcpdump examples\|tcpdump examples]]

{ .block-language-dataview}





> my java server is running on localhost 8443. i am running a krakend on 8070 which is passing he request to java server. i want to use tcpdump to inspect the request

```bash
sudo tcpdump -i any port 8070 -A
```


https://hackertarget.com/tcpdump-examples/

## Monitoring traffic from source to destination

On Destination VM:

```bash

sudo tcpdump -i any port 8065

```

On Source VM:

```bash

sudo tcpdump -i any host [destination_vm_ip] and port 8065

```


## Example 

The command:

```bash
tcpdump -i eth2 host 192.168.10.5
```

**Explanation**:

```bash
tcpdump - i eth2 host 192.168.10.5 
```

1. `-i eth2`:  
   Specifies the network interface `eth2` to listen on. If this option is omitted, `tcpdump` listens on the first active interface by default.

2. `host 192.168.10.5`:  
   Filters packets to capture only those **involving the host** with the IP address `192.168.10.5`. This includes packets **to or from** the specified host.

**Effect**:  
This command captures all packets on the `eth2` interface that are either **sent to** or **received from** the IP address `192.168.10.5`.

**Example Use Case**:  
You want to monitor traffic specifically for a machine at `192.168.10.5` on the `eth2` network interface.

