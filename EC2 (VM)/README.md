https://aws.amazon.com/ec2/
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/AMIs.html

# EC2
Amazon EC2 is a web service that provides secure, resizable compute capacity in the cloud. With this service, you can provision virtual servers called EC2 instances. 

For high availability, consider using at least two EC2 instances in two separate Availability Zones.

You must define the following: 
- Hardware specifications: 
    - Instance type: CPU, Memory and GPU (optional). Instance families: General purpose, Compute optimized, Memory optimized, Accelerated computing, Storage optimized and HPC optimized.
    - network
    - storage
- Logical configurations: 
    - Networking location
    - firewall rules
    - authentication
    - operating system (AMI)

# Amazon Machine Image (AMI)
EC2 instances are live instantiations (or versions) of what is defined in an Amazon Machine Image (AMI)
you can create an AMI from your running instance and use the AMI to start a new instance.

AMIs can comes from:
- AMIs created by AWS
- AWS Marketplace AMIs from third-party vendors
- AMIs are created from your EC2 instances.
- Community AMIs are provided by the AWS user community
- Build your own custom image with EC2 Image Builder
