- [Elastic Compute Cloud](#elastic-compute-cloud)
  - [What's EC2](#whats-ec2)
    - [EC2 Instances & AMI](#ec2-instances--ami)
  - [Amazon Machine Images](#amazon-machine-images)
    - [Root Device Volume](#root-device-volume)
    - [EBS vs Instance Store AMI](#ebs-vs-instance-store-ami)
  - [Instances](#instances)
    - [Instance Types](#instance-types)
    - [Instance Purchasing Options](#instance-purchasing-options)
    - [Instance Lifecycle](#instance-lifecycle)
  - [Network & Security](#network--security)
    - [Ssh Key Pairs](#ssh-key-pairs)
    - [Security Groups](#security-groups)
      - [CIDR Notation](#cidr-notation)
      - [NAT](#nat)
      - [Understanding purpose of Outbound Rules](#understanding-purpose-of-outbound-rules)

# [Elastic Compute Cloud](https://aws.amazon.com/ec2/)

## [What's EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/concepts.html)

It provides scalable computing capacity in the AWS cloud

### [EC2 Instances & AMI](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instances-and-amis.html)

## [Amazon Machine Images](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html)

### [Root Device Volume](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/RootDeviceStorage.html)

### [EBS vs Instance Store AMI](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ComponentsAMIs.html#storage-for-the-root-device)

## Instances

### [Instance Types](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html)

- **Instance Type** determines the hardware of the host computer used for your instance
- Types:

  - **General Purpose Instances**:

    - A balance of compute, memory, and networking resources
    - Good for following applications:
      - Web and application servers
      - Small Databases
      - Microservices
      - Development, build, test & staging environments

  - **Compute Optimized Instances**:

    - Ideal for compute bound applications which need high performance processors
    - Suited for following applications:
      - Batch Processing Workloads
      - High Performance Computing
      - Dedicated Gaming Servers
      - Ad Serving Engines
      - Machine Learning Inference

  - **Storage Optimized Instances**:

    - These are designed for workloads that require _high, sequential read and write access_ to very large data sets on local storage
    - They are optimized to deliver tens of thousands of low-latency, random I/O operations per second (IOPS) to applications
    - Suited for:
      - MapReduce and Hadoop distributed computing
      - Log or data processing applications
      - Databases (Relational and NoSQL both)
      - Data warehousing applications

  - **Accelerated Computing Instances**:

    - If you require high processing capability, use these instances
    - Provide access to hardware-based compute accelerators such as GPUs or FPGAs
    - GPU Instances accelerate:
      - Scentific & Engineering Applications
      - Rendering applications
    - FPGA Instances accelerate:
      - Genomics
      - Financial Analysis
      - Real Time Video Processing
      - Big Data Analysis

### [Instance Purchasing Options](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-purchasing-options.html)

- [On Demand](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-capacity-reservations.html):

  - Allows you to pay a fixed rate by the hour (or second) with no commitment
  - Good for applications with short term, spiky or unpredictable loads that can't be interrupted
  - Good fit for application _development_ & _testing_

- [Reserved](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-reserved-instances.html):

  - Provides you with a capacity reservation
  - Offers a significant cost saving on the hourly charge of an instance
  - Contract Terms: 1 year or 3 years
  - Good for applications with steady state or predictable usage or which require a reserved capacity

- [Spot](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-instances.html)

  - Enables you to bid whatever price you want for instance capacity
  - Useful for applications with flexible start & end times

- [Dedicated Hosts](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dedicated-hosts-overview.html):

  - Physical EC2 servers dedicated for an enterprise
  - Helps you to reduce costs by allowing you to use your existing server-bound software licenses

- [Dedicated Instances](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/dedicated-instance.html):
  - Dedicated Instances run in a VPC on hardware that's dedicated to a single customer
  - Pay, by the hour, for instances that run on single-tenant hardware

### [Instance Lifecycle](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-instance-lifecycle.html)

## Network & Security

### Ssh Key Pairs

- EC2 uses ssh to connect to instance via command prompt
- Ssh login is managed via asymmetric encryption keys where pubic key is uploaded to AWS and private key resides in your system
- All you need is to refer that private key on a terminal/secure shell to login to EC2 instance

```bash
ssh ec2-user@<instance-public-ip> -i <aws-private-key>
```

_ec2-user is default user for ec2 instances_

You could get your encryption key pair in 2 ways:

- [Creating a Key Pair using EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#having-ec2-create-your-key-pair)

  - Here, EC2 creates for the encryption keys
  - It then places _public key_ content at `~/.ssh/authorized_keys` file of the instance
  - And user sees a file dialog to download the private key (_one with .pem extension_) in their system

- [Importing Your Own Public Key to Amazon EC2](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ec2-key-pairs.html#how-to-generate-your-own-key-and-import-it-to-aws)

  - In this case, user could create his own **RSA** key pair using 3rd-party tools like `ssh-keygen`
  - This tool will generate 2 keys with same name:
    - Private key (_key with no extension_)
    - Public key (_one with .pub extension_)
  - All user needs is to import the public key to EC2 and then, use above command to login with private key

### [Security Groups](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-network-security.html)

- A security group acts as a virtual firewall that controls the traffic for one or more instances
- It controls both **inbound** as well as **outbound** traffic
- If you modify the rules for a security group at any time; the new rules are automatically applied to all instances that are associated with the security group
- Security groups are associated with network interfaces
  - Changing an instance's security groups changes the security groups associated with the primary network interface (eth0)
- Security groups are stateful
  - If you send a request from your instance, the response traffic for that request is allowed to flow in regardless of inbound security group rules
  - This also means that responses to allowed inbound traffic are allowed to flow out, regardless of outbound rules

#### [Understanding purpose of Outbound Rules](https://acloud.guru/forums/aws-csa-2019/discussion/-Ljh1TuR55bh2RzG1uk7/his_description_of_outbound_ru)
