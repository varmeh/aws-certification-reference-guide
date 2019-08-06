- [CloudFront](#cloudfront)
  - [What's a CDN](#whats-a-cdn)
    - [S3 Security & Encryption](#s3-security--encryption)
  - [Amazon Storage](#amazon-storage)
    - [Amazon Storage Gateway](#amazon-storage-gateway)
    - [Snowball](#snowball)
  - [S3 Transfer Acceleration](#s3-transfer-acceleration)
  - [Static Website Using S3](#static-website-using-s3)

# [CloudFront](https://aws.amazon.com/cloudfront/)

## [What's a CDN](https://www.cloudflare.com/learning/cdn/what-is-a-cdn/)

- A Content Delivery Network or Content Distribution Network is a geographically distributed network of proxy servers and their data centres

- Key terminology about CloudFront:
  - **Edge Location**: this is the location where the content is cached for faster delivery (_low latency is the driving force behind cdn_)
  - **Origin**: this is the source of all the files that the CDN will distribute. eg. EC2 instance, an S3 bucket, an Elastic Load Balancer, Route53 etc. You can also have your own origin, it not mandatory that is within AWS
  - **Distribution**: this is the name AWS calls CDN's. It is basically a collection of Edge Locations
    - 2 types of distribution
      - **Web Distribution**: typically for websites
      - **RTMP**: for media streaming
    - TTL: time to live of the cached object.

### [S3 Security & Encryption](https://aws.amazon.com/blogs/aws/new-amazon-s3-encryption-security-features/)

- You can configure S3 to create access logs for requests made to the S3 bucket
- Access control for buckets:

  - Bucket policies: Permission bucket wide
  - Access control list: Permissions that can be applied to the single object

- Encryption:
  - In transit: from to your bucket, HTTPS for example
  - At rest:
    - Server-side encryption:
      - S3 Managed Keys: SSE-S3 (Keys are managed by S3)
      - Key Management Service: SS3-KMS the customer manages the keys
      - Server-side encryption: Here you manage the keys, and Amazon manage the writes
  - Client-side Encryption: You encrypt the data and you upload it encrypted to S3

## [Amazon Storage](https://aws.amazon.com/products/storage/)

### [Amazon Storage Gateway](https://aws.amazon.com/storagegateway/)

What's an Amazon Storage Gateway: AWS Storage Gateway connects an on-premises software appliance with cloud-based storage to provide seamless integration with data security features between your on-premises IT environment and the AWS storage infrastructure.

- File Gateway: For flat files, stored directly in S3. You can NFS Mount points
- VOlume gateway (iSCSI): Block-based storage
  - Store volume (you keep all your data on prem)
  - Cached Volumes (you keep only the most recent data on prem)
    Tape Gateway (VTL): Virtual tapes

### [Snowball](https://aws.amazon.com/snowball/)

Import Export is still available and was the first version of snowball, you used to ship your drives to AWS

Snowball is (an appliance) a petabyte-scale data transport solution that uses devices designed to be secure to transfer large amounts of data into and out of the AWS Cloud

Snowball edge: is a 100TB data transfer device with onboard storage-computer capabilities. It's like an AWS DC in a box

Snowmobile: AWS Snowmobile is an Exabyte-scale data transfer service used to move extremely large amounts of data to AWS. A truck full of disks basically.

## [S3 Transfer Acceleration](https://docs.aws.amazon.com/AmazonS3/latest/dev/transfer-acceleration.html)

Instead of uploading files directly to your S3 bucket, you can use the AWS edge network.
Using a specific URL, you upload the file to your local edge and then the file will be uploaded to S3
an example or URL: alessio-casco-accelerate.s3-accelerate.amazonaws.com

## [Static Website Using S3](https://docs.aws.amazon.com/AmazonS3/latest/dev/HowDoIWebsiteConfiguration.html)

- You can use bucket policies to make entire S3 buckets public
- You can use S3 to host only static websites.
- S3 Scales automatically to meet demand

[Permissions Required for Website Access](https://docs.aws.amazon.com/AmazonS3/latest/dev/WebsiteAccessPermissionsReqd.html)

On console: Amazon S3 => Your_Bucket => Permissions => Bucket Policy

```json
{
	"Version": "2012-10-17",
	"Statement": [
		{
			"Sid": "PublicReadGetObject",
			"Effect": "Allow",
			"Principal": "*",
			"Action": ["s3:GetObject"],
			"Resource": ["arn:aws:s3:::example-bucket/*"]
		}
	]
}
```

_[!!! Read the S3 FAQs before the exam !!!](https://aws.amazon.com/s3/faqs/)_
