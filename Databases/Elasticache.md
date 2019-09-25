- [Elasticache](#elasticache)
  - [What is Elasticache](#what-is-elasticache)
  - [In-memory data store](#in-memory-data-store)
  - [Comparing Memcached and Redis](#comparing-memcached-and-redis)
  - [Elastic Cache vs Read Replica](#elastic-cache-vs-read-replica)

# Elasticache

## [What is Elasticache](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/WhatIs.html)

- It is a web service that makes it easy to set up, manage, and scale a distributed in-memory cache environment in the cloud
- It provides a high-performance, scalable, and cost-effective caching solution
- It improves the performance of web-applications by allowing you to retrieve from in-memory caches

## [In-memory data store](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/elasticache-use-cases.html#elasticache-use-cases-data-store)

## [Comparing Memcached and Redis](https://docs.aws.amazon.com/AmazonElastiCache/latest/red-ug/SelectEngine.html)

- Amazon ElastiCache supports the **Memcached** and **Redis** cache engines

- Prefer **Memcached** if you need:
  - `Simplest model possible`
  - `Multi-threading` - to run large nodes with multiple cores or threads
  - `Horizontal Scaling` - the ability to scale out and in, adding and removing nodes as demand on your system increases and decreases
  - to cache objects, such as a database

- Prefer **Redis** if you need:
  - `Multi-AZ ` - high availability
  - `Encryption`
  - `Compliance Certifications` - *FedRAMP*, *HIPAA* & *PCI DSS*
  - `Backup and restore`
  - `Automatic Failover`
  - `Geospatial indexing`

## [Elastic Cache vs Read Replica](https://acloud.guru/forums/aws-certified-solutions-architect-associate/discussion/-Ke_GPS6RLo8eHaXIR_t/elasticache_vs_read_replica)