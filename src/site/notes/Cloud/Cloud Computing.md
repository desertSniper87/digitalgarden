---
{"dg-publish":true,"permalink":"/cloud/cloud-computing/"}
---


## Dynamic Capacity Provisioning

### Elasticity vs Scalability

### Scalability

- Static property
- Specifies its behavior on a static configuration.
- Handled by adding resources to existing instances—called scaling up or vertical scaling

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
– Bigtable, HBase, and ElasTraS are examples.
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


### State of the art

#### Follow the workload

- [Online Dynamic Capacity Provisioning in Data Centers](http://rsrg.cms.caltech.edu/greenIT/papers/dcp-allerton.pdf)
    - how many servers to be kept active and how much workload to be delayed for energy saving while meeting every deadline. We present an offline LP formulation for capacity provisioning by dynamic deferral and give two online algorithms to determine the capacity of the data center and the assignment of workload to servers dynamically.
    - Cited by
        - [Dynamic Deferral of Workload for Capacity Provisioning in Data Centers - Adnan](https://arxiv.org/pdf/1109.3839.pdf)
        - [A 2-Competitive Algorithm For Online Convex
Optimization With Switching Costs](https://drops.dagstuhl.de/opus/volltexte/2015/5297/pdf/7.pdf)
        - [Cloud Computing Operations Research](https://www.labri.fr/perso/eyraud/pmwiki/uploads/Main/CloudOR.pdf)
        - [Characterizing the Impact of the Workload on the Value of Dynamic Resizing in Data Centers✩](https://arxiv.org/pdf/1207.6295.pdf)

- Lazy capacity provisioning (LCP)
    - h dynamically turns on/off servers in a data center to minimize energy cost and delay cost for scheduling workload
    - aims at minimizing the average delay (penalizing delay)
    - 3-competitive solution
    - no bounds on maximum delay.


#### GreenSlot 

Paper: [GreenSlot: Scheduling Energy Consumption in Green Datacenters](https://personals.ac.upc.edu/jguitart/HomepageFiles/SC11.pdf)



- Considered jobs with deadline requirement, 
- schedules jobs to maximize green energy consumption. 
- jobs may violate deadline when too many jobs are stored to execute later.




### Online Resources

- [DYNAMIC PROVISIONING AND RESOURCE MANAGEMENT FOR MULTI-TIER CLOUD BASED APPLICATIONS](https://sciendo.com/pdf/10.2478/fcds-2013-0008)
