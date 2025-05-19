https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html

- IPv4: you don’t see an IP address in its binary format. Instead, it’s converted into decimal format in octets and noted as an IPv4 address.
- CIDR: CIDR notation is a compressed way of representing a range of IP addresses. Specifying a range determines how many IP addresses are available to you. . In AWS, the smallest IP range you can have is /28, which provides 16 IP addresses. The largest IP range you can have is a /16, which provides 65,536 IP addresses.

# VPC
VPC is an isolated network that you create in the AWS Cloud, consist of: VPC name + CIDR + Region
Every instance must live inside of a VPC

- Default VPC - private network for AWS resources. Any resource that you put inside the default VPC will be public and accessible by the internet. AWS Creates VPCs in every region by Default in the Default VPC
- Custom VPCs is more secure and provide more granular access ti the internet

### Subnets
-   Subnets are used to provide high availability and connectivity options for your resources. Use a public subnet for resources that must be connected to the internet and a private subnet for resources that won't be connected to the internet.
-   Subnet consist of: VPC + Availability Zone + CIDR. 
-   A best practice to maintain redundancy and fault tolerance, create at least two subnets configured in two Availability Zones.
-   AWS reserves five IP addresses in each subnet. These IP addresses are used for: VPC local routing, Domain Name System (DNS), Future use, network broadcast address and network address.

### Security group
Security group is an instance level firewall that will allow or deny traffic to reach the instance

### Gateways
###### Internet gateway
To activate internet connectivity for your VPC, you must create an internet gateway to connect your VPC to the internet
###### Virtual private gateway
A virtual private gateway connects your VPC to another private network.
When you have both gateways, you can then establish an encrypted virtual private network (VPN) connection between the two sides.

### AWS Direct Connect
To establish a secure physical connection between your on-premises data center and your Amazon VPC, you can use AWS Direct Connect.

