---
{"dg-publish":true,"permalink":"/db/key-value-stores/percolator/"}
---

#cse6603 

## Summary

Percolator leverages application semantics to relax the performance requirements as well as the isolation guarantees sought.

## Method

![](https://miro.medium.com/max/720/1*tAuOyRBSjAtHPnKffWlEzg.png)

- Two main abstractions for [[db/Distributed Database/Incremental Update Processing|Incremental Update Processing]] at large
scale:
    - Cross-row, Cross-table transactions with ACID snapshot isolation semantics. (see Berenson et al 1995)
    - Supports the notion of observers that allow organizing incremental computation.
- Percolator is built as a layer on top of [[db/key value stores/Bigtable|Bigtable]].
- Percolator relies on a timestamp oracle 
    - Provides strictly increasing timestamps 
    - Critical for correctness of the [[db/Distributed Database/Snapshot isolation|Snapshot isolation]] protocol that **isolates concurrent update transactions**.
- A transaction begins execution by obtaining a start timestamp from the timestamp oracle.
    - This defines the consistent snapshot that the read operations of this transaction will read from.
- Updates made by a transaction are buffered during execution and will be applied when the transaction is ready to commit.
- Since a transaction can update data items distributed over a set of nodes, atomically committing the updates requires a [[two phase commit|two phase commit]] coordinated by the client.
- At each node, an update to a data item is executed using the row transaction API of Bigtable.

## See also
1. Berenson et al., 1995
2. [Implementing Distributed Transactions the Google Way: Percolator vs. Spanner | by Sid Choudhury | The Distributed SQL Blog | Medium](https://medium.com/yugabyte/implementing-distributed-transactions-the-google-way-percolator-vs-spanner-6cbccfc1f2ed)
