
![storage_portfolio](/img/storage_portfolio.png)

# Edge and hybrid cloud storage services

services that are designed to provide edge and hybrid cloud solutions. 

- AWS Snow Family
They provide a data transfer platform to copy your data in to and out from the AWS Cloud.
    - AWS Snowball devices: AWS Snowball is an edge computing, data migration, and edge storage device. 
    - AWS Snowcone devices:  Snowcone is ruggedized, secure, and purpose-built for use outside of a traditional data center. 
    - AWS Snowmobile service: AWS Snowmobile is an exabyte-scale data transfer service used to move large amounts of data to AWS

- AWS Snowpots:
AWS compute, storage, database, and other services run locally on Outposts. You can access the full range of AWS services available in the Region to build, manage, and scale your on-premises applications using familiar AWS services and tools.

- AWS Storage Gateway:
Storage Gateway offers four different types of gateways. Providing low-latency access to data in AWS for on-premises applications
    - Amazon S3 File Gateway
    - Amazon FSx File Gateway
    - Volume Gateway
    - Tape Gateway

# Data transfer and migration services
Data transfer services are designed to copy or transfer your on-premises data to and from the core AWS Storage services in the AWS Cloud. 

- AWS Transfer Family: provides fully managed support for file transfers directly into and out of Amazon S3 or Amazon EFS. AWS Transfer Family includes support for Secure File Transfer Protocol (SFTP), File Transfer Protocol over SSL (FTPS), and File Transfer Protocol (FTP). 
- AWS DataSync: Migrate active datasets to AWS. Archive data to free up on-premises storage capacity. Replicate data to AWS for business continuity. Transfer data to the cloud for analysis and processing 
- AWS Snow Family: Offline data transfers because there’s lack of consistent network connectivity.
- AWS Application Migration Service: highly automated lift-and-shift (rehost) solution.

# Data protection services
Data protection services provide optional services to meet your data redundancy and disaster requirement needs

- AWS Backup: you can centralize and automate data protection across AWS services. Centrally deploy policies to configure, manage, and govern your backup activity across your company’s AWS accounts and resources.
- Native Service Snapshot: Snapshots create backup copies of your data. Snapshots are incremental copies of the data. Each snapshot contains all of the information for that point in time that is needed to restore your data.
- CloudEndure Disaster Recovery: continuously replicates your machines into a low-cost staging area in your target AWS account and preferred Region. Minimizes downtime and data loss by providing fast, reliable recovery of physical, virtual, and cloud-based servers into AWS Cloud. 


