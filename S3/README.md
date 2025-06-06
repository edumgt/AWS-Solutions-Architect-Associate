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
- Glacier Instant Retrieval: archiving data that is rarely accessed and requires millisecond retrieval
- Glacier Flexible Retrieval: archived data that is accessed 1–2 times per year and retrieved in minutes.
- Glacier Deep Archive: lowest-cost Amazon S3 storage class. Data accessed once or twice a year with a retrieval time of 12 hours
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