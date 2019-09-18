- [Storage Gateway](#storage-gateway)
  - [What is Storage Gateway](#what-is-storage-gateway)
  - [How AWS Storage Gateway Works](#how-aws-storage-gateway-works)

# [Storage Gateway](https://aws.amazon.com/storagegateway/)

## [What is Storage Gateway](https://docs.aws.amazon.com/storagegateway/latest/userguide/WhatIsStorageGateway.html)

- It is a hybrid storage service that enables your on-premises applications to seamlessly use AWS cloud storage
- You can use the service for backup and archiving, disaster recovery, cloud data processing, storage tiering, and migration
- The service helps you reduce and simplify your datacenter and branch or remote office storage infrastructure
- Your applications connect to the service through a virtual machine or hardware gateway appliance using standard storage protocols, such as NFS, SMB and iSCSI
- The gateway connects to AWS storage services, such as Amazon S3, Amazon S3 Glacier, Amazon S3 Glacier Deep Archive, Amazon EBS, and AWS Backup, providing storage for files, volumes, snapshots, and virtual tapes in AWS
- The service includes a highly-optimized data transfer mechanism, with bandwidth management, automated network resilience, and efficient data transfer, along with a local cache for low-latency on-premises access to your most active data. 

- It offers 3 types of gateway solutions:
  - **File Gateway**: 
    - It supports a file interface into Amazon S3
    - Data transfer done using Network File System (NFS) and Server Message Block (SMB)
    - *Files stored as Objects in S3* via NFS mount point

  - **Volume Gateway**: 
    - It provides cloud-backed storage volumes
    - These volumes could be mounted as iSCSI devices (*disk drives*) on your on-premise application servers
    - *Way of storing copies of your hard drives*
    - Data is backed up to Amazon S3 as Amazon EBS snapshots
  
    - It supports following configuration:
      - **Cached volumes**: Use Amazon S3 as your primary data storage, while retaining frequently accessed data locally in your storage gateway
      - **Stored volumes**: Store primary data locally, while asynchronously backing up that data to AWS

  - **Tape Gateway**:
    - With a tape gateway, you can cost-effectively and durably archive backup data in GLACIER or DEEP_ARCHIVE

  - Gateway is deployed into your on-premise environment using virtual machines
  - Gateway manages data transfer to and from AWS, buffers applications from network congestion, optimizes and streams data in parallel, and manages bandwidth consumption


## [How AWS Storage Gateway Works](https://docs.aws.amazon.com/storagegateway/latest/userguide/StorageGatewayConcepts.html)
