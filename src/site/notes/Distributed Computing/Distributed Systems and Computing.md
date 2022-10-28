---
{"dg-publish":true,"permalink":"/distributed-computing/distributed-systems-and-computing/"}
---

See [[Distributed Computing/Clocks|Clocks]]

## Notes

### Kleppman

#### [Martin Kleppman's Lecture Notes on distributed systems](https://www.cl.cam.ac.uk/teaching/2122/ConcDisSys/dist-sys-notes.pdf)

## Mutual Exclusion

> instituted for the purpose of preventing [race conditions](https://en.wikipedia.org/wiki/Race_condition). (Wikipedia)
- Arises whenever **concurrent processes** access **shared resources**.
- Given a set of processes and a single resource, develop a **protocol** to ensure **exclusive access** to the resource by a **single process** at a time.
- A simple **centralized** solution for the distributed mutual exclusion problem is to designate ==one **process as the coordinator**==
- Maintains a **queue** of pending requests

## Leader Election

- One process to act as coordinator, and typically, *it does not matter which process is actually chosen*.

### Bully Algorithm

See, [Wikipedia](https://en.wikipedia.org/wiki/Bully_algorithm), [Bhanu Priya](https://www.youtube.com/watch?v=R1FfoED7OGo), [colostate (good example)](https://www.cs.colostate.edu/~cs551/CourseNotes/Synchronization/BullyExample.html)

- Select the process with the ==highest process-id==.
- Any process can initiate an election if
    - it just recovered from a **failure** or 
    - it suspects that the current coordinator has **failed**.
	    - Cannot communicate with leader.
- Three types of messages are used: **election**, *ok*, and ==I won==.

#### Bully Algo Steps
1. An initiating process p sends **election** messages to all processes with higher IDs and awaits for *ok* messages.
2. If a process receives an **election** message, it returns an *ok* message and starts an **election**.
    - election message comes from process of lower IDs.
    - Repeat step 1.
3. If it receives any *ok* messages, it drops out and waits for an I won message.
    - ok message comes from process having higher id.
4. If no *ok* messages are received, p becomes the coordinator and sends ==I won== to all processes with lower IDs.
5. If a process receives an ==I won== message, then the sender is the coordinator.

## Quorums

- **Distributed protocol** to overcome failures, with no central coordinator.
- Any **two requests** should have a **common process** to act as an **==arbitrator==**.
- Any **read and write** quorums must intersect, and any **two write quorums** must intersect.
 - However, read quorums do not necessarily intersect, and hence
multiple read operations can be executed concurrently.

> Solves [Split Brain](https://en.wikipedia.org/wiki/Split-brain_(computing)) / [Network partition](https://en.wikipedia.org/wiki/Network_partition)


See [[Distributed Computing/Distributed Systems and Computing#Kleppman|#Kleppman]] *5.2 Quorums*

## Paxos protocol

**Computer Algorithm**: To achieve agreement, one or more of the computers **proposes** a value to *Paxos*  (***Proposer***). **Consensus** is achieved when a majority of the computers running *Paxos* agrees **on one of the** *proposed values* (***Acceptor***).

Paxos defines several different roles from [Sylladb](https://www.scylladb.com/glossary/paxos-consensus-algorithm/):

1. ***Proposers***, who receive requests (values) from clients and try to convince **acceptors** to accept the value they propose.
2. ***Acceptors***, who accept certain proposed values from proposers and let **proposers** know whether a different value was accepted. A **response** from an **acceptor** represents a **vote** for a **particular proposal.**
	- Single acceptor.  Multiple proposers will concurrently propose various values to a single acceptor. The acceptor chooses one of these proposed values ([Understanding Paxos](https://people.cs.rutgers.edu/~pxk/417/notes/paxos.html))
3. **Learners**, who announce the outcome to all participating nodes.

![](https://www.scylladb.com/wp-content/uploads/paxos-diagram.png)

- For asynchronous systems.
- Leader-based protocol where each process has an **estimate** of _who the current leader_ is.
- When *a process* desires to achieve **consensus** on a value, it sends it to the current leader.
- The leader launches a **consensus algorithm** to ensure agreement.


### consensus algorithm 

From ([understanding paxos](https://www.cs.rutgers.edu/~pxk/417/notes/paxos.html))/6603 Lectures/[martinfowler](https://martinfowler.com/articles/patterns-of-distributed-systems/paxos.html)

**Phase 0**

Client asks a leader/proposer for a value.

**Phase 1 (Prepare)**

A **proposer** asks all the working **acceptors** whether anyone *already received a proposal*. If the answer is no, **propose a value**.

- Choose new ballot number (establish latest genaration clock)
- Send new ballot to sites and wait for ack (along with result of previous votes)

**Phase 2 (Accept)**

- After receiving ack, propose value with ballot
- If a majority of **acceptors** agree to this value then that is our consensus.

### Resources

#### [Paxos - Wikipedia](https://en.wikipedia.org/wiki/Paxos_(computer_science))

**Paxos** is a _family of protocols_ for solving [consensus](https://en.wikipedia.org/wiki/Consensus_(computer_science) "Consensus (computer science)") in a network of _unreliable_ or _fallible_ processors.

- Paxos is usually used where _durability is required_


#### [The Part-Time Parliament - Leslie Lamport](http://lamport.azurewebsites.net/pubs/lamport-paxos.pdf)

#### [What is Paxos Consensus Algorithm? Definition & FAQs | ScyllaDB](https://www.scylladb.com/glossary/paxos-consensus-algorithm/)

#### [Understanding Paxos](https://www.cs.rutgers.edu/~pxk/417/notes/paxos.html)

#### [Paxos - martin fowler](https://martinfowler.com/articles/patterns-of-distributed-systems/paxos.html)

Three phases. 
-   **Prepare phase**: establish the latest [Generation Clock](https://martinfowler.com/articles/patterns-of-distributed-systems/generation.html) and gather any already accepted values.
    - **Leader** chooses a new unique ballot number, which is sent to all sites, 
    - Waits to learn the outcome of all smaller ballots from a majority of sites.
-   **Accept phase**: propose a value for this generation for replicas to accept.
-   **Commit Phase**: let all the replicas know that a value has been chosen.

[What is Paxos Consensus Algorithm? Definition & FAQs | ScyllaDB](https://www.scylladb.com/glossary/paxos-consensus-algorithm/)

---
See also, [[Distributed Computing/Books/bytebytego|bytebytego]]

## Peer To Peer Systems

- An overlay organizes: 
    - the way different sites **communicate** with each other
    - the **storing of data objects** at the different sites.
- Overlays provide a method for retrieving objects, and typically support two basic operations using a key value pair:
    - **Set**: Insert the key-value tuple in the overlay.
    - **Get**: lookup and return the corresponding value using key.
- Overlays are typically represented as a graph,
    - Sites as nodes, 
    - Edges connecting these sites,
    - Categorized into:
        - **Unstructured** overlays.
        - **Structured** overlays.

### Unstructured Overlays

No specific structure on logical graph between the peers.

- Napster
- Gnutella


### Structured Overlays

Structured overlays
- Impose a well-defined data structure on the various peers.
- Distributed Hash Tables (DHTs), which maps objects to
sites, and provides methods for efficiently retrieving
an object, given its corresponding key.
- Edges are chosen according to some rule, and data is
stored at pre-defined sites.
- each site also maintains a table that defines the next-
hop for lookup operations.

- DHT (Distributed Hash Tables)
- [BitTorrent - Wikipedia](https://en.wikipedia.org/wiki/BitTorrent)


See, [[Distributed Computing/Consistent Hashing|Consistent Hashing]]
