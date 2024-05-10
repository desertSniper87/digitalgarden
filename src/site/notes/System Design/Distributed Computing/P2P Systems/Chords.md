---
{"dg-publish":true,"permalink":"/system-design/distributed-computing/p2-p-systems/chords/"}
---


#cse6603 

![](https://miro.medium.com/max/640/0*XV4B_fIkmiIU7Gbp.png)

## Introductory Paper

[Chord: A Scalable Peer-to-peer Lookup Service for Internet Applications](https://pdos.csail.mit.edu/papers/chord:sigcomm01/chord_sigcomm.pdf)

## Theory

**Chord** is a protocol and [algorithm](https://en.wikipedia.org/wiki/Algorithm "Algorithm") for a [peer-to-peer](https://en.wikipedia.org/wiki/Peer-to-peer "Peer-to-peer") [distributed hash table](https://en.wikipedia.org/wiki/Distributed_hash_table)

### Problem

In a peer-to-peer network, data is stored in different computers. A user needs to find out which computer the data is stored at before accessing it.

### Solution

- Nodes (each computer in the network) and keys are assigned an **m-bit** identifier using [[System Design/Distributed Computing/Consistent Hashing\|Consistent Hashing]].
	- There are $2^m$ Ids available
	- if m=8, total possible ids =  $2^8$ = 256
- The SHA-1 algorithm is the base hashing function for consistent hashing
- Using the Chord lookup protocol, nodes and keys are arranged in an identifier circle that has at most $2^m (0$ to $2^m-1)$ nodes.

![Pasted image 20221029013246.png](/img/user/attachments/Pasted%20image%2020221029013246.png)

- Sites are then organized in a logical ring according to their IDs.
- Keys are also hashed into the same identifier space, and the key (and the corresponding value) is stored at its successor, i.e., the node with next higher ID.
- The expected number of hops is O(log n) where n is the number of nodes in the Chord ring.


![](https://miro.medium.com/max/500/0*WqXs3F73o7NGlXuJ.png)


### Avoiding the linear $O(n)$ search [--source](https://medium.com/techlog/chord-building-a-dht-distributed-hash-table-in-golang-67c3ce17417b)


![](https://miro.medium.com/max/720/0*ma9nP6ZPZ2OwEvvN.png)




## Implementation

### [Chord: Building a DHT (Distributed Hash Table) in Golang | by Farhan Ali Khan | techlog | Medium](https://medium.com/techlog/chord-building-a-dht-distributed-hash-table-in-golang-67c3ce17417b)

### [GitHub - mitul227/Chord-DHT: Implementation of Chord P2P Distributed Hash Table](https://github.com/mitul227/Chord-DHT)

## Further reading 

### [Chord - Wikipedia](https://en.wikipedia.org/wiki/Chord_(peer-to-peer))

### [Key lookup in Chord with finger table | by Jing Yang | Medium](https://medium.com/@jingyang_56841/key-lookup-in-chord-with-finger-table-c0179bafae13)

