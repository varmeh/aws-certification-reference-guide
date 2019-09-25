- [Aurora](#aurora)
  - [What is Aurora](#what-is-aurora)
  - [Aurora DB Clusters](#aurora-db-clusters)
  - [Storage](#storage)
  - [High Availability](#high-availability)

# Aurora

## [What is Aurora](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/AuroraUserGuide/CHAP_AuroraOverview.html)

- It is a fully managed relational database engine that's compatible with MySQL and PostgreSQL
- Aurora is part of the managed database service Amazon RDS

## [Aurora DB Clusters](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.html)

- **Aurora DB cluster**: consists of one or more DB instances and a cluster volume that manages the data for those DB instances
- **Aurora cluster volume**: a virtual database storage volume that spans multiple Availability Zones, with each Availability Zone having a copy of the DB cluster data
- Each Aurora DB cluster can have up to 15 Aurora Replicas
- Maintain high availability by locating Aurora Replicas in separate Availability Zones
- Aurora automatically fails over to an Aurora Replica in case the primary DB instance becomes unavailable

## [Storage](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/AuroraUserGuide/Aurora.Overview.StorageReliability.html)

- [Aurora Replicas](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/AuroraUserGuide/Aurora.Replication.html)

## [High Availability](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/AuroraUserGuide/Concepts.AuroraHighAvailability.html)

- Aurora stores copies of the data in a DB cluster across multiple Availability Zones in a single AWS Region