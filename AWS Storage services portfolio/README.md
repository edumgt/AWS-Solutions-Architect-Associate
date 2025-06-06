
![storage_portfolio](/img/storage_portfolio.png)

# Edge and hybrid cloud storage services
AWS edge computing services provide infrastructure and software that move data processing and analysis to where you are located. AWS hybrid cloud solutions and services help you run and manage your applications wherever they may need to reside. 
services that are designed to provide edge and hybrid cloud solutions. 

- AWS Snow Family
They provide a data transfer platform to copy your data in to and out from the AWS Cloud.
    - AWS Snowball devices: AWS Snowball is an edge computing, data migration, and edge storage device. 
    - AWS Snowcone devices:  Snowcone is ruggedized, secure, and purpose-built for use outside of a traditional data center. devices are small
        Job Types:
        - Local compute and storage only
        - Import into Amazon S3: for data collection and local processing. When you return the device to AWS, your data is uploaded to your Amazon S3 bucket
        - Export from Amazon s3: After the device arrives, you copy data from your device to your local storage
    - AWS Snowmobile service: AWS Snowmobile is an exabyte-scale data transfer service used to move large amounts of data to AWS

![snowball_and_snowcone](/img/snowball_and_snowcone.jpg)

- AWS Snowpots:
AWS compute, storage, database, and other services run locally on Outposts. You can access the full range of AWS services available in the Region to build, manage, and scale your on-premises applications using familiar AWS services and tools. An Outpost is a pool of AWS compute and storage capacity deployed at a site.
Suports EC2, ECS, RDS, EBS, EKS and also S3.

    Use case:
    - to meet application latency requirements, Outposts help you run applications where you need them to be located.
    - You can set up a consistent hybrid cloud architecture to process data on premises and easily move data to the cloud for long-term archival.
    - for regulatory, contractual, or information security reasons. 

- AWS Storage Gateway:
Storage Gateway offers four different types of gateways. Providing low-latency access to data in AWS for on-premises applications
    - Amazon S3 File Gateway
    - Amazon FSx File Gateway
    - Volume Gateway (Amazon EBS snapshots)
    - Tape Gateway
The local gateway appliance maintains a cache of recently written or read data so that your applications can have low-latency access to data that is stored durably in AWS.  As a native AWS service, Storage Gateway integrates with other AWS services for storage, backup, and management while still integrating with on-premises environments. 

# Data transfer and migration services
Data transfer services are designed to copy or transfer your on-premises data to and from the core AWS Storage services in the AWS Cloud. 

- AWS Transfer Family: provides fully managed support for file transfers directly into and out of Amazon S3 or Amazon EFS. AWS Transfer Family includes support for Secure File Transfer Protocol (SFTP), File Transfer Protocol over SSL (FTPS), and File Transfer Protocol (FTP). AWS helps you migrate your file transfer workflows to AWS by integrating with existing authentication systems, and providing DNS routing with Amazon Route 53. Features:
    - A fully managed service that scales in real time to meet your needs.
    - You don't need to modify your applications or run any file transfer protocol infrastructure.
    - Store the files you exchange as objects in your Amazon S3 bucket or Amazon EFS file system so that you can extract business insights faster.
    - you pay for only the protocols you have enabled for access to your endpoint and the amount of data transferred over each of these protocols.
    ![dataTransfer_infraestructure](/img/dataTransfer_infraestructure.png)
- AWS DataSync: Migrate active datasets to AWS. Archive data to free up on-premises storage capacity. Replicate data to AWS for business continuity. Transfer data to the cloud for analysis and processing 
- AWS Snow Family: Offline data transfers because there’s lack of consistent network connectivity.
- AWS Application Migration Service: highly automated lift-and-shift (rehost) solution.

# Data protection services
Data protection services provide optional services to meet your data redundancy and disaster requirement needs

- AWS Backup: you can centralize and automate data protection across AWS services. Centrally deploy policies to configure, manage, and govern your backup activity across your company’s AWS accounts and resources.
- Native Service Snapshot: Snapshots create backup copies of your data. Snapshots are incremental copies of the data. Each snapshot contains all of the information for that point in time that is needed to restore your data.
- CloudEndure Disaster Recovery: continuously replicates your machines into a low-cost staging area in your target AWS account and preferred Region. Minimizes downtime and data loss by providing fast, reliable recovery of physical, virtual, and cloud-based servers into AWS Cloud. 


