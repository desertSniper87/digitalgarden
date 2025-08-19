---
{"dg-publish":true,"permalink":"/mac-flooding/"}
---

- Overwrite fields in switch
- [MAC flooding](https://en.wikipedia.org/wiki/MAC_flooding)

Switches maintain a [[CAM Table\|translation table]] that maps various [[MAC Address\|MAC Addresses]] to the physical ports on the switch
- As a result, they can intelligently route packets from one host to another
- However, switches have a limited memory
- MAC flooding makes use of this limitation to bombard switches with fake MAC addresses until the switches can no longer keep up
- Once this happens to a switch, it will enter **fail-open mode**, wherein it starts acting as a hub by broadcasting packets to all the ports on the switch
	- It can no longer store new **MAC addresses** that it learns from incoming frames.
	- When a switch receives a frame from a **source MAC address** that it doesn’t know (i.e., it’s not in the CAM table), and the table is full, the switch will **flood the frame** out of all ports except the one it came from. ==Swich is now working as a [[Hub\|Hub]]==
- Once that happens, it becomes easy to perform sniffing


## Tools

- [[macof\|macof]] is a utility that comes with the [[dsniff\|dsniff]] suite and helps the attacker to perform MAC flooding.

