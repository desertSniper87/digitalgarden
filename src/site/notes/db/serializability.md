---
{"dg-publish":true,"permalink":"/db/serializability/","dgPassFrontmatter":true}
---

- Given a set of transactions, we are guaranteed correctness if they
are executed serially.
- To allow some degree of concurrency among transactions, the notion
of serializability was developed.
- A set of transactions is serializable if it is equivalent to a serial history
over the same set of transactions.
