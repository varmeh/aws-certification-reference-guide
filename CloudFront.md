- [CloudFront](#cloudfront)
  - [What is CloudFront?](#what-is-cloudfront)
  - [Key Terminology](#key-terminology)
  - [Use Cases](#use-cases)
  - [How CloudFront Delivers Content](#how-cloudfront-delivers-content)
  - [Getting Started](#getting-started)
  - [Distributions](#distributions)
  - [Content Management](#content-management)
    - [Updating Content in Edge Locations](#updating-content-in-edge-locations)
    - [Invalidating Files](#invalidating-files)
    - [Managing Cache Expiration](#managing-cache-expiration)
  - [Good to Know](#good-to-know)
  - [Misc Questions](#misc-questions)

# [CloudFront](https://aws.amazon.com/cloudfront/)

## [What is CloudFront?](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Introduction.html)

- CloudFront is a Content Delivery Network [(CDN)](https://www.cloudflare.com/learning/cdn/what-is-a-cdn/)
- A CDN is a system of distributed servers (*network*) that delivers web content to a user based on geographic location of user

## Key Terminology

  - **Edge Location**: 
    - This is the location where the content is cached for faster delivery (_low latency is the driving force behind CDN_)
    - This is seperate from *AWS Regions* & *Availability Zones*
    - When a user requests content that you're serving with CloudFront, the user is routed to the edge location that provides the lowest latency
    - Edge locations are NOT READ only - you could write to them too (*uploading an object is permissible e.g. Transfer Acceleration*)
    - Objects are cached for **TTL** (Time To Live)
    - By default, CloudFront caches files in edge locations for 24 hours
    - **Invalidating the cache is charged**: You can clear cached object but you will be charged for it
    - It could be used to deliver both dynamic & static web sites alongside streaming & interactive content
  
  - **Origin**: 
    - This is the origin of all the files that the CDN will distribute. eg. *EC2 instance*, *an S3 bucket*, *an Elastic Load Balancer*, *Route53* etc
    - You can also have your own origin, it not mandatory to be a AWS Service

  - **Distribution**: a collection of Edge Locations
    - 2 types of distribution
      - **Web Distribution**: typically for websites
      - **RTMP**: for media streaming

## [Use Cases](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/IntroductionUseCases.html)

## [How CloudFront Delivers Content](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/HowCloudFrontWorks.html)

## [Getting Started](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/GettingStarted.html)

## [Distributions](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/distribution-overview.html)

## Content Management

### Updating Content in Edge Locations

- CloudFront distributes files to edge locations only when the files are requested, not when you put new or updated files in your origin
- If you update an existing file in your origin with a newer version that has the same name, an edge location won't get that new version from your origin until both of the following occur:
  - The old version of the file in the cache expires
  - There's a user request for the file at that edge location

### [Invalidating Files](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Invalidation.html)

- Invalidate files from Edge locations to remove it immediately
- You cannot invalidate objects that are served by an RTMP distribution

### [Managing Cache Expiration](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/Expiration.html)

- Reducing the content TTL allows you to serve dynamic or updated content
- Increasing the duration means your users get better performance because your files are more likely to be served directly from the edge cache
  - A longer duration also reduces the load on your origin

## Good to Know

Following topics are NOT important for certification

- [Serving Compressed Files](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/ServingCompressedFiles.html)

- [Optimizing High Availability with CloudFront Origin Failover](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/high_availability_origin_failover.html)

  - Create an *origin group* with atleast 2 origins
  - Set one as primary
  - If primary fails for any reason, distribution starts using others as 

- [Lambda@Edge](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/lambda-at-the-edge.html)

- [Identity and Access Management in CloudFront](https://docs.aws.amazon.com/AmazonCloudFront/latest/DeveloperGuide/auth-and-access-control.html)


## Misc Questions

- [S3 Transfer Acceleration vs CDN](https://acloud.guru/forums/aws-csa-2019/discussion/-Lis1MjuGCKWM5CnFeRD/transfer_acceleration_for_down)
