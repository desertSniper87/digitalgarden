---
{"dg-publish":true,"permalink":"/cloud/multitenancy/"}
---

## Guides

### 1. [What is multitenancy? | Multitenant architecture | Cloudflare](https://www.cloudflare.com/learning/cloud/what-is-multitenancy/)

In [cloud computing](https://www.cloudflare.com/learning/cloud/what-is-the-cloud/), **multitenancy** means that multiple customers of a cloud vendor are using the same computing resources. Despite the fact that they share resources, cloud customers aren't aware of each other, and their *data is kept totally separate*.

### 2. [IaaS vs. PaaS vs. SaaS | Redhat](https://www.redhat.com/en/topics/cloud-computing/iaas-vs-paas-vs-saas)

![Iaas vs paas vs saas](https://www.redhat.com/cms/managed-files/iaas-paas-saas-diagram5.1-1638x1046.png)

### 3. [Database Multi-Tenancy For SaaS | lighttag](https://www.lighttag.io/blog/database-multi-tenancy/) 

There are three multi-tenancy models: Database, Schema, and Table.

#### 1. **Database multi-tenancy** (==Shared Hardware== / IaaS)

- In an exemplary implementation, the _application_ has no _concept of tenants_.

![](https://www.lighttag.io/static/02cf3240c52ce2094f67498f767b969a/fcda8/db_diagram.png)

- Tenant databases only share the **server hardware resources**.
- A virtual machine (**VM**) created host **each tenant’s database**.
- Each tenant is assigned its own VM and an exclusive database process that serves the tenant’s database.
- Predominantly used in Infrastructure-as-a-Service (***IaaS***) cloud providers such as Amazon web services (ec2)
- ***Disadvantage***
    - Increased overhead due to **redundant components**
    - **lack of coordination** using **limited machine resources** in a non-optimal
    way.
    - The co-located database processes make un-coordinated accesses to the disk.
- ***Advantage***
    - multi-tenancy can be supported ==without any changes in database layer==.

#### 2. **Schema multi-tenancy** (==Shared Process== / PaaS)

- Application connects to a database once and has _some logic_ to choosing _which schema_ to connect to when serving a particular tenant.

![](https://www.lighttag.io/static/990b4b1a9cffdb9494bd2828928286d6/2b727/schema_diagram.png)

- Tenants share resources within a **single database process** running at each server.
- This multi-tenancy model is typically observed on **PaaS** cloud providers such as Microsoft SQL Azure, Google Megastore, etc.
- ***Advantage***
    - More **effective sharing** of some of the ==critical physical resources== such as **I/O and main memory**
    - ensuring *a level of* **isolation** of user data in separate tables.
- ***Disadvantages***
    - Does not support the notion of elasticity that would allow dynamic migration of databases hosted at one DBMS instance to another DBMS.
    - DBMSs become **sluggish** when a large number of tenant databases are hosted especially when **workload spikes**.


#### 3. **Table multi-tenancy** (==Shared Table== / SaaS)

- _every row_ in every table is _associated with a given tenant._

![](https://www.lighttag.io/static/dd3c42f9c140a5b1224c379f8cd8096c/6bdcf/table_diagram1.png)

- In the shared table model, the tenants’ data are stored in a shared table called the **heap table**.
- To support flexibility in schema and data types across the different tenants, the heap table does not contain the tenant’s schema or column information.
- ***Disadvantage***
    - requires that all tenants reside on the same database engine and release
    - Limits specialized database functionality, such as spatial or object based, and
    requires that all tenants use a limited subset of functionality.
- ***Advantage***
    - This multi-tenancy model is ideal when multiple tenants have **similar schema** and access patterns with minimal customizations, thus providing ==effective sharing of resources==.
    - Such similarity is observed in SaaS where a **generic application tenant** is *customized* to meet specific customer requirements.
