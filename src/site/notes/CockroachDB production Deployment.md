---
{"dg-publish":true,"permalink":"/cockroach-db-production-deployment/"}
---


## Time Sync

1. CockroachDB requires moderate levels of clock synchronization to preserve data consistency
	1. [Deploy CockroachDB On-Premises | CockroachDB Docs](https://www.cockroachlabs.com/docs/v22.1/deploy-cockroachdb-on-premises#step-1-synchronize-clocks)

## Sizing

1. The size of your cluster corresponds to its total number of vCPUs.
	1. A **smaller number of larger nodes** emphasizes cluster stability
	2. A **larger number of smaller nodes** emphasizes resiliency across [failure scenarios](https://www.cockroachlabs.com/docs/v22.1/disaster-recovery).

## Reference

1. [Production Checklist | CockroachDB Docs](https://www.cockroachlabs.com/docs/stable/recommended-production-settings.html)
2. [Deploy CockroachDB On-Premises | CockroachDB Docs](https://www.cockroachlabs.com/docs/v22.1/deploy-cockroachdb-on-premises)