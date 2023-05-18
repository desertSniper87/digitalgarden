---
dg-publish: true
---

#cse6603 

## Dynamic Capacity Provisioning

### Elasticity vs Scalability

### Scalability

- Static property
- Specifies its behavior on a static configuration.
- Handled by adding resources to existing instances - called scaling up or vertical scaling

### Elasticity 

- Dynamic property
- Grow or shrink infrastructure resources in an autonomic manner.

####  [Cloud Elasticity vs. Cloud Scalability: What's the Difference? | IBM](https://www.ibm.com/cloud/blog/cloud-elasticity-vs-cloud-scalability)

### Challenges

#### Engineering Challenges
- Reliability
- Migration 

##### **Live Database Migration**

While being elastic, the system must also ensure that a tenant’s performance or service goals are not violated.

Live migration for the two most common cloud database
architectures:

###### shared disk
• Shared disk architectures are attractive for their ability to
abstract replication, fault-tolerance, and consistency, as well as
their support for independent scaling of the storage layer from
the DBMS logic.
– [[db/key value stores/Bigtable\|Bigtable]], HBase, and [[ElasTraS\|ElasTraS]] are examples.
• Shared nothing multi-tenant architecture, such as Relational

###### shared nothing.
Shared nothing multi-tenant architecture, such as Relational
Cloud and Cloud SQL Server, uses locally attached storage for
storing persistent data and are common in database design.
– Live migration for a shared nothing architecture requires
that all database components are migrated between nodes,
including physical storage files.

#### Algorithmic Challenges
- Characterizing offline **optimal solutions**
- Proposing **online algorithm** for **right-sizing**
    - Guarantee performance in the worst case
    - Nearly optimal in realistic settings.


### State of the art solutions

1. [[Cloud/Dynamic Capacity Provisioning/Follow the workload\|Follow the workload]]


#### GreenSlot 

Paper: [GreenSlot: Scheduling Energy Consumption in Green Datacenters](https://personals.ac.upc.edu/jguitart/HomepageFiles/SC11.pdf)



- Considered jobs with deadline requirement, 
- schedules jobs to maximize green energy consumption. 
- jobs may violate deadline when too many jobs are stored to execute later.




### Online Resources

- [DYNAMIC PROVISIONING AND RESOURCE MANAGEMENT FOR MULTI-TIER CLOUD BASED APPLICATIONS](https://sciendo.com/pdf/10.2478/fcds-2013-0008)


## Distributed Databases in the cloud

See [[db/Distributed Database/Transactions\|Transactions]]

## [[Cloud/Multitenancy\|Multitenancy]]

– SaaS and PaaS cloud infrastructures typically serve
hundreds of thousands of small applications (called
tenants)
– Dedicating a DBMS server for each tenant is often wasteful
since the individual tenants’ resource requirements are
often small.
– In order to reduce the total cost of operation, cloud
providers typically share resources among the tenants, a
model referred to as [[Cloud/Multitenancy\|multitenancy]].