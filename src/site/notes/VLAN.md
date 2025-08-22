---
{"dg-publish":true,"permalink":"/vlan/"}
---

A `VLAN` is a **logical grouping of network** endpoints connected to **defined ports on a switch**, allowing the segmentation of networks by **creating logical broadcast domains** that can span multiple physical LAN segments.
- With `VLANs`, network administrators can segment networks based on factors such as team, function, department, or application, without worrying about the physical location of endpoints and users.
- A broadcast packet sent over one `VLAN` does not reach any other endpoint that is a member of another `VLAN`.
- Because each `VLAN` is regarded as a broadcast domain, it needs to have its own `subnet`; for example, the network administrator contracted by XQ can segment the network by departments:

| **Department** | **VLAN ID** |    **Subnet**    |
| :------------: | :---------: | :--------------: |
|   `Servers`    |  `VLAN 10`  | `192.168.1.0/24` |
|   `C-Level`    |  `VLAN 20`  | `192.168.2.0/24` |
|   `Finance`    |  `VLAN 30`  | `192.168.3.0/24` |
|      `HR`      |  `VLAN 40`  | `192.168.4.0/24` |
|  `Marketing`   |  `VLAN 50`  | `192.168.5.0/24` |
|   `Support`    |  `VLAN 60`  | `192.168.6.0/24` |
## VLAN Identification

Standard `802.3` `Ethernet` frames do not contain `VLAN` information; therefore, switches and other `VLAN`-enabled devices need a mechanism to keep track of all the `VLAN` information associated with a packet while traversing `VLAN`-enabled devices. Two main `trunking methods` are utilized to achieve this, `ISL` and `IEEE 802.1Q`.

 
<div class="transclusion internal-embed is-loaded"><a class="markdown-embed-link" href="/802-1-q/" aria-label="Open link"><svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="svg-icon lucide-link"><path d="M10 13a5 5 0 0 0 7.54.54l3-3a5 5 0 0 0-7.07-7.07l-1.72 1.71"></path><path d="M14 11a5 5 0 0 0-7.54-.54l-3 3a5 5 0 0 0 7.07 7.07l1.71-1.71"></path></svg></a><div class="markdown-embed">

<div class="markdown-embed-title">

# IEEE 802.1Q

</div>



To ensure interoperability of `VLAN` technologies from the various network-equipments vendors, the `Institute of Electrical and Electronics Engineers` (`IEEE`) developed the [802.1Q](https://ieeexplore.ieee.org/document/10004498) specification in 1998.
- The `IEEE 802` committee had to change the [[IEEE 802.3\|IEEE 802.3]] `Ethernet` frame format by adding a pair of 2-byte fields, `TPID` and `TCI` (which consists of three subfields, `PCP`, `DEI`, and `VID`), resulting in a `VLAN`-compliant `802.1Q` `Ethernet` frame.

![Diagram showing conversion of a 802.3 Ethernet frame to a 802.1Q Ethernet frame by inserting a 802.1Q header between the source address and length fields. The 802.1Q header includes TPID, PCP, DEI, and VID.](https://academy.hackthebox.com/storage/modules/34/8023_Legacy_8021Q_Ethernet_Frames.png)



</div></div>



#### Assigning NICs a VLAN in Linux

```shell-session
sudo modprobe 8021q
```

```shell-session
lsmod | grep 8021
```

```shell-session
sudo vconfig add eth0 20
```