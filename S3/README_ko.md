TODO: translate
https://aws.amazon.com/s3/

# Blob Storage
In object storage, data is stored as objects in buckets.
Objects are treated as a single, distinct unit of data when stored. 
Each object contains a unique identifier. This identifier, along with any additional metadata, is bundled with the data and stored.
Changing just one character in an object is more difficult than with block storage. When you want to change one character in an object, the entire object must be updated.

### Use Case
you can store almost any type of data, and there is no limit to the number of objects stored, which makes it readily scalable. Object storage is generally useful when storing large or unstructured data sets.
- Data archiving: long-term data retention
- Backup and recovery: replicate content so that if a physical device fails
- Rich media: By using storage classes and replication features, you can create cost-effective, globally replicated architecture to deliver media to distributed users.

# Amazon Simple Storage Service (Amazon S3)

 Amazon S3 uses standards-based REST APIs designed to work with any internet-development toolkit. 
you can retrieve your data from anywhere on the web.
Object storage stores data in a flat structure. An object is a file combined with metadata.
S3 is highly available with data replication across availability zones
Each bucket name must be unique across all AWS accounts in all AWS Regions within a partition
The object key (key name) uniquely identifies the object in an Amazon S3 bucket. 

Features:
- Moving and storing data across different S3 storage classes
- Configuring and enforcing data access controls
- Appending metadata tags to objects
- Monitoring data at the object or bucket levels
- Viewing storage usage and activity trends across your organization
- Amazon S3 performance supports at least 3,500 requests per second to add data and 5,500 requests per second to retrieve data. Each S3 prefix can support these request rates, making it simple to increase performance significantly.
- You can also enforce write-once-read-many (WORM) policies with S3 Object Lock. You can configure S3 Object Lock in one of two modes: Governance mode and Compliance mode (no user or root account can remove the protection). 
- **S3 Storage Lens** includes drill-down options to generate insights at the organization, account, Region, bucket, or even prefix level.
- Amazon S3 is also compatible with AWS analytics services such as Amazon Athena and Amazon Redshift Spectrum (complex queries and large datasets). you can run big data analytics directly on your data stored in Amazon S3. It works by retrieving a subset of an object’s data instead of the entire object, 


Use case:
- Backup, Archive and storage: back up files because it is highly redundant
- media hosting: ideal location to host video, photo, and music uploads.
- Software delivery: host your software applications that customers can download.
- Data lakes: because of its virtually unlimited scalability. AWS Lake Formation to quickly create a data lake and centrally define and enforce security, governance, and auditing policies
- Static website and content: host a static website and static content
- The solution is also ideal for importing existing data stores for analytics, backup, or archive.
- Websites and Mobile applications
- IoT devices
- with AWS PrivateLink, you can provision private endpoints in a VPC to allow direct access to S3 from on-premises using private IPs from your VPC. 

Security:
- Amazon S3 is private by default.
- You can choose to make your buckets and objects public. 
- Amazon S3 Server access logging provides detailed records for the requests that are made to a bucket. or use CloudTrail provides event history of your AWS account activity, including actions taken through the AWS Management Console, AWS SDKs, command line tools, and other AWS services.
- Controlled access (with access policy):
    - IAM Policy: which are attached to resources and users
    - S3 bucket policies: This can only be attached to S3 buckets. S3 bucket policies specify what actions are allowed or denied on the bucket.
    - Encryption: Amazon S3 reinforces encryption in transit (as it travels to and from Amazon S3) and at rest. 

![S3_Bucket_Access](/img/S3_Bucket_Access.png)

Storage Classes
Amazon S3 storage classes let you change your storage tier when your data characteristics change.
![s3_storage_classes](/img/s3_storage_classes.jpg)

- Standard: this is the default storage class. general-purpose storage
- S3 Intelligent-Tiering: Amazon S3 monitors access patterns of your data and automatically moves your data to the most cost-effective storage tier based on frequency of access. There are three tiers: a frequent access tier, an infrequent access tier, and an archive instance access tier.
- Standard-Infrequent Access: data that is accessed less frequently but requires rapid access when needed
- One Zone-Infrequent Access: lower-cost option for infrequently accessed data, but do not require the availability and resilience of S3 Standard or S3 Standard-IA
- Glacier Instant Retrieval: archiving data that is rarely accessed and requires millisecond retrieval with a fee per GB. Data is stored across three or more AWS Availability Zones.
- Glacier Flexible Retrieval: archived data that is accessed 1–2 times per year and retrieved in minutes. Data is stored across three or more AWS Availability Zones. Minimum storage duration of 90 days. There are two types: 
    - Free bulk retrievals (5h - 12h) 
    - non-bulk retrievals (Expedited with 1-5 min and Standard with 3-5 h) with a Retrieval fee per GB. 
- Glacier Deep Archive: lowest-cost Amazon S3 storage class. Data accessed once or twice a year with a retrieval time of 12 hours and retrieval fee per GB. Data is stored across three or more AWS Availability Zones. Minimum duration requirement of 180 days of storage
- S3 on Outposts: Amazon S3 on Outposts delivers object storage to your on-premises AWS Outposts environment using S3 API's and features


Versioning
Without Amazon S3 versioning, every time you upload an object with the same name to the bucket, it will overwrite the original object.
Versioning keeps multiple versions of a single object in the same bucket. 
Versioning helps with object recovery from accidental deletions, accidental overwrites, or application failures.
To reduce your Amazon S3 bill, you might want to delete previous versions of your objects when they are no longer needed.
Buckets can be in one of three states:
- Unversioned (default)
- Versioning-enable: After you version-enable a bucket, it can never return to an unversioned state
- Versioning-suspended: Versioning is suspended for new objects.

Amazon S3 lifecycle:
You can choose to automate between two types of actions: transition (to another storage class) and expiration (deleted).
![Storage_Lifecycle](/img/Storage_Lifecycle.png)

S3 Batch Operations:
- Copy objects between buckets
- Replace object tag sets
- Modify access controls,
- Restore archived objects from Amazon S3 Glacier

# S3 Cost Optimization

- You need to understand your workloads, and define your application performance and data access requirements. 
- Organizing data allows you to filter groups of objects together for optimized storage and analysis by tags, prefixes, or both. An effective organization strategy improves data visibility by allowing granular and precise insights into your usage and cost spending based on your applications, projects, or teams
- Knowing your data access patterns allows you to make informed decisions about which storage class best suits your data, for performance and cost.
    - Predictable workloads: Amazon S3 Storage Class Analysis to  how much of your data is hot, warm, and cold. It also provides daily visualizations of your storage usage on the AWS Management Console that you can export to an S3 bucket to analyze using business intelligence tools of your choice like Amazon Quicksigth. 
    You can analyze objects based on:
        - Bucket
        - Prefixes and tags
        - Exports
    Knowing this usage information allows you to configure an S3 Lifecycle policy to make the data transfer to the appropriate storage class and saving costs in the way.
    A lifecycle policy is a rule that moves or delete objects between storage classes based on the object create date.
    ![s3_life_cycle](/img/s3_life_cycle.jpg)
    Amazon S3 does not transition objects between storage classes if they are smaller than 128 KB because it's not cost effective to do so.
    - Unpredictable workloads: Amazon S3 Intelligent-Tiering
-  Knowing which storage class your data currently occupies is the first step in identifying if the storage class is the right storage class for your data.

Tips:
- Using Amazon S3 inventory, Amazon S3 Server access logging and AWS CloudTrail together allows you to determine if objects are being put to S3, but never accessed. Once that determination is made, objects that are never accessed can be moved to archived tiers for storage cost savings.
- Objects in S3 Intelligent-Tiering, S3 Standard-IA, and S3 One Zone-IA storage are charged for a minimum storage duration of 30 days
- Multipart uploads accelerate the uploading of large objects (size is over 100 MB) by splitting them into parts that are then uploaded in parallel. A Lifecycle rule can be configured to automatically remove incomplete uploads.
- With S3 Glacier you can retain more data for longer periods of time at a lower storage cost
- AWS Storage Gateway allows businesses with on-premises data centers to use Amazon S3 for backups or long-term retention.
- Amazon S3 Storage Lens provides organization-wide visibility into object storage usage and activity trends. S3 Storage Lens provides metrics pre-aggregated by up to six levels, beginning with the account, Region, storage class, and bucket.  You can  use the default or custom dashboard to visualize insights and trends, flag outliers, and it provides recommendations for optimizing storage costs and applying data protection best practices. 
- Alarms allow you to watch CloudWatch metrics and to receive notifications when the metrics fall outside of the levels (high or low thresholds) that you configure. You can attach multiple alarms to each metric and each one can automatically initiate actions on your behalf. 
- AWS Budgets gives you the ability to set custom budgets that alert you when your costs or usage exceed (or are forecasted to exceed) your budgeted amount.
