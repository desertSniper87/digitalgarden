---
{"dg-publish":true,"permalink":"/system-design/distributed-computing/clocks/clocks/"}
---

#cse6603 

## References

### http://infolab.stanford.edu/~burback/dadl/node93.html

> In a distributed system, communication between elements is ==inherently asynchronous==.

### https://en.wikipedia.org/wiki/Lamport_timestamp

>The **Lamport timestamp** algorithm is a simple ==[logical clock algorithm](https://en.wikipedia.org/wiki/Logical_clock_algorithm "Logical clock algorithm")== used to determine the order of events in a [distributed computer system](https://en.wikipedia.org/wiki/Distributed_computer_system "Distributed computer system").

### Youtube Videos

#### [Martin Kleppmann](https://www.youtube.com/watch?v=x-D8iFU1d-o)

See, [[System Design/Distributed Computing/Distributed Systems and Computing#Kleppman|Distributed Systems and Computing#Kleppman]]

> Distributed Systems 4.1: Logical time

[Logical vs physical Clocks](https://youtu.be/x-D8iFU1d-o?t=68)
 > Physical Timestamps: Inconsistent with causality
 > Logical Clocks: **Capture causal dependencies**
 
See, [[System Design/Distributed Computing/Clocks/Lamport Clock|Lamport Clock]]


See, [Vector Clocks](https://youtu.be/x-D8iFU1d-o?t=670)


### 6603 Lecture Notes

Distributed systems are also classified into synchronous and asynchronous systems.

• In an **asynchronous distributed** system
- no bounds are known on the times for message
transmission, processor processing, or on local clock drifts.
• In a **synchronous system**
- such bounds are known, and hence timeout can be used to
detect failures, and when needed, act accordingly.
