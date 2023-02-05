---
{"dg-publish":true,"permalink":"/db/distributed-database/sql/cockroach-db/cockroach-db-production-deployment/"}
---


## Time Sync

1. CockroachDB requires moderate levels of clock synchronization to preserve data consistency
	1. [Deploy CockroachDB On-Premises | CockroachDB Docs](https://www.cockroachlabs.com/docs/v22.1/deploy-cockroachdb-on-premises#step-1-synchronize-clocks)

## Sizing

1. The size of your cluster corresponds to its total number of vCPUs.
	1. A **smaller number of larger nodes** emphasizes cluster stability
	2. A **larger number of smaller nodes** emphasizes resiliency across [failure scenarios](https://www.cockroachlabs.com/docs/v22.1/disaster-recovery).

## Deploying in a single node

### Creating certificate for the node

Creating the certificate and key for the first node:

```bash
cockroach cert create-node \
172.16.221.243 \
172.16.221.243 \
keycloak-poc  \
localhost \
127.0.0.1 \
172.16.221.226 \
haproxy-poc  \
--certs-dir=/data/certs \
--ca-key=/data/certs/ca.key
```




Creating the certificate and key for the Second node:

```bash
cockroach cert create-node \
172.16.221.230 \
172.16.221.230 \
keycloak-poc  \
localhost \
127.0.0.1 \
172.16.221.226 \
haproxy-poc  \
--certs-dir=/data/certs \
--ca-key=/data/certs/ca.key
```


## Load Balancer ([[sre/server_deployment/Haproxy\|Haproxy]]) Config

```cfg
listen psql
    bind :26257
    mode tcp
    balance roundrobin
    option httpchk GET /health?ready=1
    server cockroach1 <node1 address>:26257 check port 8080
    server cockroach2 <node2 address>:26257 check port 8080

```


## Reference

1. [Production Checklist | CockroachDB Docs](https://www.cockroachlabs.com/docs/stable/recommended-production-settings.html)
2. [Deploy CockroachDB On-Premises | CockroachDB Docs](https://www.cockroachlabs.com/docs/v22.1/deploy-cockroachdb-on-premises)
3. [Linux Installation](https://www.cockroachlabs.com/docs/v22.1/install-cockroachdb-linux.html)
4. [Deploy CockroachDB On-Premises | CockroachDB Docs](https://www.cockroachlabs.com/docs/stable/deploy-cockroachdb-on-premises.html)
5. [How To Deploy CockroachDB on a Three-Node Cluster on Ubuntu 16.04 | DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-deploy-cockroachdb-on-a-three-node-cluster-on-ubuntu-16-04)
