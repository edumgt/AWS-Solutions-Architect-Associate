TODO: translate
https://aws.amazon.com/efs/
https://aws.amazon.com/fsx/

# File Storage
In file storage, data is stored as files in a tree-like hierarchy that consist of folders and subfolders. 
Each file has metadata such as file name, file size, the creation date and a path. 
When you need to retrieve a file, your system can use the path to find it in the file hierarchy.
The two most common storage protocols for file storage are Server Message Block (SMB) and Network File System (NFS).

### Use Case:
Ideal when you require centralized access to files that must be easily shared and managed by multiple host computers.
This storage is typically mounted onto multiple hosts, and requires file locking and integration with existing file system communication protocols.

- Web serving: When the develop a web requires file-level protocols, file naming conventions, and permissions that developers are familiar with
- Analytics: analytics workloads which interact with data through a file interface and rely on features such as file lock or writing to portions of a file.
- Media and entertainment: businesses that use a hybrid cloud deployment and need standardized access using file system protocols (NFS or SMB) or concurrent protocol access
- Home directories: Businesses wanting to take advantage of the scalability and cost benefits of the cloud are extending access to home directories for many of their users.

### Services
- Amazon Elastic File System (Amazon EFS)
- Amazon FSx for Lustre
- Amazon FSx for NetApp ONTAP
- Amazon FSx for OpenZFS
- Amazon FSx for Windows File Server

# Amazon Elastic File System (Amazon EFS)
The service uses a traditional file permissions model, file locking, and hierarchical directory structure using the NFSv4 protocol. 
File system that automatically grows and shrinks as you add and remove files. Amazon EFS file systems can automatically scale from gigabytes to petabytes of data without needing to provision storage
Amazon EFS can be used with AWS compute services and on-premises resources.
You pay only for the storage used.
Tens, hundreds, or even thousands of compute instances can access an Amazon EFS file system at the same time.
All files and directories are redundantly stored within and across multiple Availability Zones by default
Serveless
Multiple compute modules can access an Amazon EFS file system at the same time. These modules include include Amazon EC2, AWS Lambda, AWS Fargate, Amazon Elastic Container Service (Amazon ECS), and Amazon Elastic Kubernetes Service (Amazon EKS). 

Storage classes:
You pay only for the storage used by your file system. No minimum fee and no set-up charges are incurred. 
- Standard storage classes: offer Multi-AZ resilience and the highest levels of durability and availability.
- One zone storage classes: provide additional savings by saving your data redundantly in a single availability zone.

Features:
- Supports authentication, authorization, and encryption capabilities to help you meet your security and compliance requirements. 
- With EFS lifecycle management policies enabled, files automatically move from Amazon EFS Standard storage to EFS Standard-IA storage, or from Amazon EFS One Zone storage to EFS One Zone-IA storage. Lifecycle management reduces storage costs by up to 92 percent.
- Security: Security groups and IAM 
- On-premise can access through VPN or Direct connect to EFS

Use case:
- Migrate enterprise applications from on premises to the AWS Cloud
- machine learning and big data analytics workloads. 
- Media workflows often depend on shared storage to manipulate large files. Example workflows include video editing, studio production, broadcast processing, sound design, and rendering. 

Modes:
- The default General Purpose performance mode is ideal for latency-sensitive use cases
- The default Bursting Throughput mode, throughput scales as your file system grows.

# Amazon FSx
native compatibility with third-party file systems

With Amazon FSx, you can choose between four widely used file systems: 
- Amazon FSx for Lustre is an AWS fully managed parallel file system built on Lustre for high performance computing (HPC) workloads. FSx for Lustre supports the Lustre POSIX-compliant protocol. Use: machine learning, video processing, and financial modeling.
- Amazon FSx for NetApp ONTAP is the NetApp ONTAP operating system implemented as a fully managed service. FSx for NetApp ONTAP support iSCSI for block storage, NFS protocol for POSIX-compliant access, and SMB protocol for Windows-compatible access.
- Amazon FSx for OpenZFS is an AWS fully managed implementation of the Open Zettabyte File System (ZFS). FSx for OpenZFS supports NFS and SMB protocols for a wide range of application implementations. 
- Amazon FSx for Windows File Server is an AWS fully managed file system for Windows environments. FSx for Windows File Server supports the Server Message Block (SMB) protocol.
- Using Amazon EC2 and Amazon EBS, you can quickly create your own high-performance block storage for building your own network file system, including the following protocols and systems:
    - SMB
    - NFS
    - Extents File System (XFS) 
    - General Parallel File System (GPFS)
    - Zettabyte File System (ZFS)
    - Other customer files systems
