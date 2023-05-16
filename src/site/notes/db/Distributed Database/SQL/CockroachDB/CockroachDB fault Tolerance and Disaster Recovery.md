---
{"dg-publish":true,"permalink":"/db/distributed-database/sql/cockroach-db/cockroach-db-fault-tolerance-and-disaster-recovery/","dgPassFrontmatter":true}
---


## Fault Tolerance

When a node fails, the cluster waits for the node to remain offline for 5 minutes by default before considering it dead, at which point the cluster automatically repairs itself by re-replicating any of the replicas on the down nodes to other available nodes.

## Disaster Recovery

### Hardware Failure
### Data Failure



## Reference

1. [Fault Tolerance & Recovery | CockroachDB Docs](https://www.cockroachlabs.com/docs/v22.1/demo-fault-tolerance-and-recovery)
2. [Disaster Recovery | CockroachDB Docs](https://www.cockroachlabs.com/docs/stable/disaster-recovery.html#data-failure)
3. [Basic Production Topology | CockroachDB Docs](https://www.cockroachlabs.com/docs/v22.1/topology-basic-production#configuration)