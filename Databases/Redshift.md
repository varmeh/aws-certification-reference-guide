- [Redshift](#redshift)
  - [What is Redshift](#what-is-redshift)
  - [Data Warehousing Basics](#data-warehousing-basics)
    - [OLTP vs OLAP](#oltp-vs-olap)
    - [Tutorial](#tutorial)
  - [Amazon Redshift Clusters](#amazon-redshift-clusters)
    - [Clusters and Nodes in Amazon Redshift](#clusters-and-nodes-in-amazon-redshift)
    - [Regions and Availability Zone Considerations](#regions-and-availability-zone-considerations)
  - [Data Warehouse System Architecture](#data-warehouse-system-architecture)
  - [Backup](#backup)
  - [Pricing](#pricing)

# Redshift

## [What is Redshift](https://docs.aws.amazon.com/en_pv/redshift/latest/mgmt/welcome.html)

- Amazon Redshift is a fully managed, petabyte-scale data warehouse service in the cloud
- Used for OLAP (Online Analytical Processing)
- The first step to create a data warehouse is to launch a set of nodes, called an **Amazon Redshift cluster**
- After you provision your cluster, you can upload your data set and then perform data analysis queries

## Data Warehousing Basics

### [OLTP vs OLAP](https://techdifferences.com/difference-between-oltp-and-olap.html)

### [Tutorial](https://www.tutorialspoint.com/dwh/dwh_overview.htm)

Read only following sections:
- Overview
- Concepts

## Amazon Redshift Clusters

- An Amazon Redshift data warehouse is a collection of computing resources called `nodes`
- The nodes are organized into a group called a `cluster`
- Each cluster runs an Amazon Redshift engine and contains one or more databases

### [Clusters and Nodes in Amazon Redshift](https://docs.aws.amazon.com/en_pv/redshift/latest/mgmt/working-with-clusters.html#rs-about-clusters-and-nodes)

- An Amazon Redshift cluster consists of nodes
- Each cluster has a **leader node** and **one or more compute nodes**
- **Leader node** 
  - It receives queries from client applications, parses the queries, and develops query execution plans
  - The leader node then `coordinates the parallel execution` of these plans with *the compute nodes* and aggregates the intermediate results from these nodes
  - It then finally returns the results back to the client applications

- **Compute Node**
  - execute the query execution plans and transmit data among themselves to serve these queries
  - The intermediate results are sent to the leader node for aggregation

- [Redshift Databases](https://docs.aws.amazon.com/en_pv/redshift/latest/mgmt/overview.html#rs-overview-databases)

### [Regions and Availability Zone Considerations](https://docs.aws.amazon.com/en_pv/redshift/latest/mgmt/working-with-clusters.html#az-considerations)

Available only in 1 AZ (No diaster recovery)

## [Data Warehouse System Architecture](https://docs.aws.amazon.com/redshift/latest/dg/c_high_level_system_architecture.html)


Advanced Compression - Column based compression for same type compression

Massive Parallel Processing (MPP): distributes data & query load across all nodes

## [Backup](https://docs.aws.amazon.com/en_pv/redshift/latest/mgmt/working-with-snapshots.html)

- Enabled by default with 1 day retention period
- Maintains 3 copies of your data:
  - the Original & the replica on compute nodes
  - a backup in Amazon S3
- Redshift could asychronously replicate your snapshots to S3 in another region for disaster recovery
- Amazon Redshift automatically takes incremental snapshots that track changes to the cluster since the previous automated snapshot

## Pricing

- Charged for compute nodes only. NO charges for leader node
- Billed for 1 unit per node per hour
- Charges for backup
- Data Transfer in VPC
