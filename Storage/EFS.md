- [Elastic File Storage](#elastic-file-storage)
  - [What is EFS](#what-is-efs)
  - [How it works](#how-it-works)
  - [EFS Storage Classes](#efs-storage-classes)
  - [Questions](#questions)
    - [S3 vs EBS vs EFS](#s3-vs-ebs-vs-efs)

# Elastic File Storage

## [What is EFS](https://docs.aws.amazon.com/efs/latest/ug/whatisefs.html)

- EFS is a file storage service for EC2 instances
- It's a Block based storage which grows and shrinks automatically as you add & remove files
- Multiple Amazon EC2 instances can access an Amazon EFS file system at the same time, unlike EBS
- Supports NFSv4 (*Network File System version 4*)
- Data stored across multiple AZ within region

## [How it works](https://docs.aws.amazon.com/en_pv/efs/latest/ug/how-it-works.html)

## [EFS Storage Classes](https://docs.aws.amazon.com/en_pv/efs/latest/ug/storage-classes.html)

## Questions

### [S3 vs EBS vs EFS](https://www.cloudberrylab.com/resources/blog/amazon-s3-vs-ebs-vs-efs/)
