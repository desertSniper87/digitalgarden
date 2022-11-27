---
{"dg-publish":true,"permalink":"/db/distributed-database/sql/cockroach-db/"}
---


1. A [[db/database|database]] that automatically scales, rebalances, and repairs itself.

## Links
1. [[db/Distributed Database/SQL/CockroachDB/CockroachDB production Deployment|CockroachDB production Deployment]]
2. [[db/Distributed Database/SQL/CockroachDB/CockroachDB fault Tolerance and Disaster Recovery|CockroachDB fault Tolerance and Disaster Recovery]]
3. [[db/Distributed Database/SQL/CockroachDB/CockroachDB Backup and Restore|CockroachDB Backup and Restore]]

## Sample workload (for testing)

1. [cockroach workload | CockroachDB Docs](https://www.cockroachlabs.com/docs/v22.1/cockroach-workload)

```bash
cockroach workload init ycsb --splits=50 'postgresql://root@localhost:26000?sslmode=disable'
```

## Support

1. [Cockroach Labs](https://support.cockroachlabs.com/hc/en-us)

## Forums

1. [r/CockroachDB](https://www.reddit.com/r/CockroachDB/)
2. [Newest 'cockroachdb' Questions - Database Administrators Stack Exchange](https://dba.stackexchange.com/questions/tagged/cockroachdb)
3. [Newest 'cockroachdb' Questions - Stack Overflow](https://stackoverflow.com/questions/tagged/cockroachdb)
4. [Join the CockroachDB Slack community | Cockroach Labs](https://www.cockroachlabs.com/join-community/?&utm_source=reddit&utm_medium=social)
	1. [Slack](https://app.slack.com/client/TP86H0JSH)
5. [Discussions · cockroachdb/cockroach · GitHub](https://github.com/cockroachdb/cockroach/discussions)
6. [Issues · cockroachdb/cockroach · GitHub](https://github.com/cockroachdb/cockroach/issues)

## Reference

1. [Quickstart with CockroachDB | CockroachDB Docs](https://www.cockroachlabs.com/docs/cockroachcloud/quickstart.html)
2. [What Geopartioning or distributed SQL database can I use? - Database Administrators Stack Exchange](https://dba.stackexchange.com/questions/234797/what-geopartioning-or-distributed-sql-database-can-i-use/234815#234815)
3. [DistributedSQL Database | Cockroach Labs](https://www.cockroachlabs.com/product/sql/)
4. [CockroachDB: The Resilient Geo-Distributed SQL Database](http://muratbuffalo.blogspot.com/2022/03/cockroachdb-resilient-geo-distributed.html)
5. [https://dl.acm.org/doi/pdf/10.1145/3318464.3386134](https://dl.acm.org/doi/pdf/10.1145/3318464.3386134)
6. [CockroachDB 2.0 Has Arrived!](https://www.cockroachlabs.com/blog/cockroachdb-2-0-release/)
7. [How We Built a Vectorized Execution Engine](https://www.cockroachlabs.com/blog/how-we-built-a-vectorized-execution-engine/)
8. [Exploring Column Families in CockroachDB - DEV Community 👩‍💻👨‍💻](https://dev.to/jordanlewis/exploring-column-families-in-cockroachdb-kje)
9. [The One Crucial Difference Between Spanner and CockroachDB](https://authzed.com/blog/prevent-newenemy-cockroachdb/)

### Videos

1. [CockroachDB: The Definitive Guide • Ben Darnell & Guy Harrison • GOTO 2022 - YouTube](https://www.youtube.com/watch?v=YGdrlRqJsJo&list=PLEx5khR4g7PJbSLmADahf0LOpTLifiCra&t=22s)

## Books

1. [CockroachDB: The Definitive Guide — Learn to Build What Can’t Be Killed](https://www.cockroachlabs.com/guides/oreilly-cockroachdb-the-definitive-guide/)