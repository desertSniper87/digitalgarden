---
{"dg-publish":true,"permalink":"/db/2-phase-locking/"}
---


[**Two-phase locking - Wikipedia**](https://en.wikipedia.org/wiki/Two-phase_locking) 

In [databases](https://en.wikipedia.org/wiki/Database "Database") and [transaction processing](https://en.wikipedia.org/wiki/Transaction_processing "Transaction processing"), **two-phase locking** (**2PL**) is a [concurrency control](https://en.wikipedia.org/wiki/Concurrency_control "Concurrency control") method that guarantees [[db/serializability|serializability]]


![](https://www.researchgate.net/profile/Muhammad-Haroon-56/publication/340476882/figure/fig2/AS:877567884156929@1586239896391/Two-phase-locking-protocol-2PL.jpg)


![](https://www.tutorialspoint.com/assets/questions/media/53993/protocol.jpg)



1.  **Growing Phase:** New locks on data items may be acquired but none can be released.
2.  **Shrinking Phase:** Existing locks may be released but no new locks can be acquired.


Two major types of locks are used:

-   **Write-lock** (**exclusive lock**) is associated with a database object by a transaction (Terminology: "the transaction locks the object," or "acquires lock for it") before _writing_ (inserting/modifying/deleting) this object.
-   **Read-lock** (**shared lock**) is associated with a database object by a transaction before _reading_ (retrieving the state of) this object.


## Further Reading

- [Explain about two phase locking (2PL) protocol(DBMS)](https://www.tutorialspoint.com/explain-about-two-phase-locking-2pl-protocol-dbms)
- [Two Phase Locking Protocol - GeeksforGeeks](https://www.geeksforgeeks.org/two-phase-locking-protocol/)
- [What is two-phase locking?](https://www.educative.io/answers/what-is-two-phase-locking)
- [Site Unreachable](https://www.javatpoint.com/dbms-lock-based-protocol)