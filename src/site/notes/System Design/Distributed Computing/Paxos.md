---
{"dg-publish":true,"permalink":"/system-design/distributed-computing/paxos/","tags":["cse6603"]}
---



- [[System Design/Distributed Computing/Paxos - Interesting Links\|Paxos - Interesting Links]]

# Paxos Protocol

**Computer Algorithm**: To achieve agreement, one or more of the computers **proposes** a value to *Paxos*  (***Proposer***). **Consensus** is achieved when a majority of the computers running *Paxos* agrees **on one of the** *proposed values* (***Acceptor***).

Paxos defines several different roles (from [Sylladb](https://www.scylladb.com/glossary/paxos-consensus-algorithm/)):

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

![Pasted image 20221101000405.png](/img/user/attachments/Pasted%20image%2020221101000405.png)

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



