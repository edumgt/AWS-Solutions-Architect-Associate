TODO: translate
https://aws.amazon.com/ebs/

# Block Storage
In block storage, data is stored in fixed-size blocks that have their own addresses.
Because each block is addressable, blocks can be retrieved efficiently and directly.
When data is requested, the addresses are used by the storage system to organize the blocks in the correct order to form a complete file to present back to the requestor.
If you want to change one character in a file, you just change the block, or the piece of the file, that contains the character.

### Use case
block storage is optimized for low-latency operations, high-performance enterprise workloads and transactional, mission-critical, and I/O-intensive applications.
- Transactional workloads: transactional and fault-tolerant database
- Containers: store containerized applications on the cloud
- Virtual machines: supports popular virtual machine (VM) hypervisors
- The storage device is used by the operating system or an application that has the capabilities to manage block storage directly. 
- databases or ERP systems
![EC2_Instacne_Block_Storage.png](/img/EC2_Instacne_Block_Storage.png)

# Amazon EC2 instance store

Amazon Elastic Compute Cloud instance store provides temporary block-level storage for an instance.
This storage is located on disks that are physically attached to the host computer and cannot be detached from Amazon EC2
This ties the lifecycle of the data to the lifecycle of the EC2 instance.
Instance store is ideal if you host applications that replicate data to other EC2 instances or cluster-based workloads
EBS can only be attahced to EC2 instances
An instance store provides submillisecond latencies between the EC2 instance and the storage.
Instance store type depends on the type of the EC2 instance

Use case:
- Temporary storage of information that changes frequently, such as buffers, caches, scratch data, and other temporary content
- Data that is replicated across a fleet of instances, such as a load-balanced pool of web servers

# Amazon EBS
Amazon Elastic Block Store is block-level storage that you can attach to an Amazon EC2 instance like an external drive. 
it is automatically replicated in its Availability Zone to prevent data loss from single points of failure
Amazon EBS provides the ability to create backups of any EBS volume.
EBS snapshots are incremental backups that only save the blocks on the volume that have changed after your most recent snapshot. Snapshots are stored redundantly in multiple Availability Zones using Amazon S3. 
Snapshot is a good way to take point-in-time backups of your data. 
The same snapshot can be used to instantiate as many volumes as you want.
EBS can only be attahced to EC2 instances
For throughput and transaction-intensive workloads at any scale. 
AWS recommends Amazon EBS for data that must be quickly accessible and requires long-term persistence.
persist independently from the life of the instance
With AWS Backup, you can centralize and automate data protection across multiple Amazon EBS volumes

Features:
- Detachable: You can detach an EBS volume from one EC2 instance and attach it to another EC2 instance in the same Availability Zone to access the data on it.
- Distinct: The external drive is separate from the computer. That means that if an accident occurs and the computer goes down, you still have your data on your external drive. The same is true for EBS volumes.
- Size-limited: You’re limited to the size of the external drive, because it has a fixed limit to how scalable it can be.
- 1-to-1 connection: Most external drives can only be connected with one computer at a time. 

You can scale EBS volumes in two ways:
- Increase the volume size only if it doesn’t increase above the maximum size limit
- Attach multiple volumes to a single EC2 instance. You can add these additional volumes during or after EC2 instance creation

Use case:
- Lift and shift on-premises applications 
- OS: Boot and root volumes can be used to store an operating system
- Databse (SQL & NoSQL): As a storage layer for databases running on Amazon EC2
- Business-critical applications.
- EBS allows you to resize clusters for big data analytics.
- Resize Spark clusters for Analytics workloads
- File systems on top of EBS

Types:
- SSD: frequent read/write operations with small I/O size. Transactional workloads, such as databases, virtual desktops, and boot volumes 
- HDD: large streaming workloads. throughput-intensive workloads, such as MapReduce and log processing. 

Pricing:
Pricing for EBS volumes is based on the volume type, provisioned volume size, and the provisioned IOPS and throughput performance. EBS volume pricing varies based on the Availability Zone where it resides. The pricing for Amazon EBS snapshots is based on the actual amount of storage space that you use.
