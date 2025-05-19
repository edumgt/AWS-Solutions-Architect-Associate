https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html

- IPv4: you don’t see an IP address in its binary format. Instead, it’s converted into decimal format in octets and noted as an IPv4 address.
- CIDR: CIDR notation is a compressed way of representing a range of IP addresses. Specifying a range determines how many IP addresses are available to you. . In AWS, the smallest IP range you can have is /28, which provides 16 IP addresses. The largest IP range you can have is a /16, which provides 65,536 IP addresses.

# VPC

Every instance must live inside of a VPC
Default VPC - private network for AWS resources.When you want launch public ec2 instances. Any resource that you put inside the default VPC will be public and accessible by the internet

Security group is an instance level firewall that will allow or deny traffic to reach the instance

Custom VPCs is more secure and provide more granular access ti the internet

AWS Creates VPCs in every region by Default in the Default VPC
