---
{"dg-publish":true,"permalink":"/macof/"}
---


macof is a network attack tool that is part of the **dsniff** suite, often used for [[MAC Flooding\|MAC flooding]]. It floods a local network with Ethernet frames that spoof different MAC addresses. The goal of this attack is to overload the MAC address table of network switches, causing them to behave like hubs and broadcast traffic to all connected devices. This is a method used to intercept traffic on a local area network ([[Local Area Network\|LAN]]).


```bash
macof -i eth0 -n 10
```