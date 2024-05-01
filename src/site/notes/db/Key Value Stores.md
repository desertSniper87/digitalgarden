---
dg-publish: true
---
#cse6603 

- Low cost scalable DBMSs
    - Google’s Bigtable 
    - Yahoo!’s PNUTS 
    - Amazon’s [[db/key value stores/Dynamo\|Dynamo]] 
- Supports
    - Simple key-value-based data model
    - ==Single atomic key-value access guarantees.==


## Data Model

- Each record is identified by a unique key, and the value can vary in its structure:
    - *Blob Data Model*: the value is a **binary string object**, i.e., a blob.
    - *Relational Data Model*: the value is structured into multiple columns, each with its own attribute name. 
	    - *@question: Is null value permitted?*
    - *Column Family Data Model*: the columns in the value field are grouped together into column families, each consisting of a set of columns.
        - Example: Bigtable, [[db/key value stores/Cassandra\|Cassandra]], HBase

## Data Distribution

For flexible scaling out to multiple servers
- In general, a table is partitioned into **tablets** (similar to **shards** or **chunks**), which form the units of *distribution* and *load balancing*.
- The two main approaches:
    - **Range partitioning**:
        - Orders all records lexicographically _based on the key_, then divides the objects on **different servers** in that order.
    - **Hash partitioning**:
        - Hashes the records **based on the key** to **linear address space**, which is then divided among the different servers.
        - A typical hashing approach can use a distributed hash table (DHT) such as Chord.

## [[Fault Tolerance\|Fault Tolerance]]

## [[db/Distributed Database/Transactions\|Transactions]]
## [[db/Distributed Database/Incremental Update Processing\|Incremental Update Processing]] 
## [[db/Distributed Database/Data Co-Location\|Data Co-Location]]




## Further Reading

- [Key-value database - Wikipedia](https://en.wikipedia.org/wiki/Key%E2%80%93value_database)
