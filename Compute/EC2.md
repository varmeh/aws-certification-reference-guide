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
