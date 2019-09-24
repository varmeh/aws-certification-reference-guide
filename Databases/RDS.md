- [Relational Database Service](#relational-database-service)
  - [What's Amazon RDS](#whats-amazon-rds)
  - [DB Instances](#db-instances)
    - [DB instance storage](#db-instance-storage)
    - [Multi-AZ](#multi-az)
    - [Read Replicas](#read-replicas)
  - [Backups](#backups)
  - [DB Monitoring](#db-monitoring)
  - [Security](#security)
    - [Encryption](#encryption)
    - [Security Groups](#security-groups)
    - [Amazon Virtual Private Cloud VPCs and Amazon RDS](#amazon-virtual-private-cloud-vpcs-and-amazon-rds)

# Relational Database Service

## [What's Amazon RDS](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/Welcome.html)

Web Service to set up, operate and scale a relational database in the AWS Cloud

Benefits of RDS:

- You could scale either of CPU, memory, storage, IOPS independent to others
- Amazon RDS manages backups, software patching, automatic failure detection, and recovery 
- To deliver a managed service experience, Amazon RDS doesn't provide shell access to DB instances
- You can have automated backups performed when you need them, or manually create your own backup snapshot
- For disater recovery, use Multi-AZ deployment
- For higher performance, you could create *Read Replicas*

## [DB Instances](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/Overview.DBInstance.html)

- A DB instance is an isolated database environment in the AWS Cloud
- It can contain multiple user-created databases
- You can have up to 40 Amazon RDS DB instances
- Each DB has an *instance identifier*
- Each DB instance runs a DB engine. Supported Engines:
  - MySQL
  - MariaDB
  - PostgreSQL
  - Oracle
  - Microsoft SQL Server

**DB instance identifier**: this customer-supplied name uniquely identifies the DB instance when interacting with the Amazon RDS API and AWS CLI commands and thus, must be unique for that customer in an AWS Region

### [DB instance storage](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/CHAP_Storage.html) 
- It comes in 3 types:
  - Magnetic
  - General Purpose (SSD)
  - Provisioned IOPS (PIOPS)

### [Multi-AZ](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/Concepts.MultiAZ.html)

- It allows to have an exact copy of your production database in another availability zone
- AWS handles replication
- It's primarily for Disaster Recovery. In case of planned maintenance, DB Instance failure or AZ failure, RDS will automatically failover to the standby

### [Read Replicas](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/USER_ReadRepl.html)

- It provides high performance by reducing load on your source db by routing read queries to *read replicas*
- Used for scaling
- `Must have automatic backups turned on` in order to deploy a read replica
- Upto 5 RR allowed for each database
- You can have read replicas of read replicas (*watchout for latency issues*)
- Each RR has it's `own DNS endpoint`. So, you need to re-direct your application to these replicas to gain performance benefits
- RR can have multiple-AZ
- RR could be promoted to their database. This breaks replication
- You could have RR in a different region 

## Backups

- Backups creates a storage volume snapshot of your DB instance, backing up the entire DB instance and not just individual databases
- 2 types of backups:
  - [**Automated Backups**](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/USER_WorkingWithAutomatedBackups.html)
    - Allow you to recover your db to any point within a `retention period` which could be as high as 35 days
    - Automated backups take `a incrementat snapshot`, including transaction logs 
    - Enabled by default with a default rentention period of 1 day
    - Automated backups occur daily during the preferred backup window
    - Backup data is stored in S3
    - You get free storage space equal to the size of your database

  - [**Database Snapshots**](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/USER_CreateSnapshot.html)
    - Mannual
    - They are stored even after db instance is deleted, unlike automated backups
  
- [Restoring a DB Instance](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/CHAP_Tutorials.RestoringFromSnapshot.html)

## [DB Monitoring](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/MonitoringOverview.html)

## [Security](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/UsingWithRDS.html)

### Encryption

- [**Encrytion at Rest**](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/Overview.Encryption.html)
  - Encrypt your Amazon RDS DB instances and snapshots at rest by enabling the encryption option for your Amazon RDS DB instance
  - Data that is encrypted at rest includes the underlying storage for DB instances, its automated backups, Read Replicas, and snapshots

- [**Encryption in Transit**](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/inter-network-traffic-privacy.html)
  
  - Encrypt traffic between
    - `Service and On-Premises Clients and Applications` with an
      - [Site-to-Site VPN](https://docs.aws.amazon.com/vpn/latest/s2svpn/VPC_VPN.html)
      - [AWS Direct Connection](https://docs.aws.amazon.com/directconnect/latest/UserGuide/Welcome.html)
    
    - `AWS Resources in the Same Region`

### [Security Groups](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/Overview.RDSSecurityGroups.html)

- Security groups control the access that traffic has in and out of a DB instance
- *Rules apply to inbound traffic only* 
- Outbound traffic is not currently permitted for DB instances
- By default, network access is disabled for a DB instance
- You can specify rules in a security group that allow access from an IP address range, port, or EC2 security group
- 2 types of Security group used with RDS:
  - **DB security group**: Controls access to EC2-Classic DB instances that are not in a VPC
  - **VPC security group**: controls access to DB instances and EC2 instances inside a VPC

### [Amazon Virtual Private Cloud VPCs and Amazon RDS](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/USER_VPC.html)

- [**EC2-Classic vs EC2-VPC**](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/USER_VPC.FindDefaultVPC.html)
- [**VPC for a DB Instance**](https://docs.aws.amazon.com/en_pv/AmazonRDS/latest/UserGuide/USER_VPC.Scenarios.html)

