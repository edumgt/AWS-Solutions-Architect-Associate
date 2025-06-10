https://docs.aws.amazon.com/vpc/latest/userguide/default-vpc.html

- IPv4: you don’t see an IP address in its binary format. Instead, it’s converted into decimal format in octets and noted as an IPv4 address.
- CIDR: CIDR notation is a compressed way of representing a range of IP addresses. Specifying a range determines how many IP addresses are available to you. . In AWS, the smallest IP range you can have is /28, which provides 16 IP addresses. The largest IP range you can have is a /16, which provides 65,536 IP addresses.
- For communications between Amazon VPC, hub-and-spoke topologies(opens in a new tab) are preferred over many-to-many mesh(opens in a new tab)

# VPC
VPC is an isolated network that you create in the AWS Cloud, consist of: VPC name + CIDR + Region
Every instance must live inside of a VPC

- Default VPC - private network for AWS resources. Any resource that you put inside the default VPC will be public and accessible by the internet. AWS Creates VPCs in every region by Default in the Default VPC
- Custom VPCs is more secure and provide more granular access ti the internet

## Subnets
-   Subnets are used to provide high availability and connectivity options for your resources. Use a public subnet for resources that must be connected to the internet and a private subnet for resources that won't be connected to the internet.
-   Subnet consist of: VPC + Availability Zone + CIDR. 
-   A best practice to maintain redundancy and fault tolerance, create at least two subnets configured in two Availability Zones.
-   AWS reserves five IP addresses in each subnet. These IP addresses are used for: VPC local routing, Domain Name System (DNS), Future use, network broadcast address and network address.
-   Subnets are created in Availability Zone level and can be more than one in each AZ.
-   CIDR provides more granular control of the number of addresses you assign to each subnet.

## Route Table
A route table contains a set of rules, called routes, that are used to determine **where network traffic is directed**.
Route Table can be attached to a subnet. Not to a VPC
#### Main route table
- When you create a VPC, AWS creates a route table called the main route table. 
- The default configuration of the main route table is to allow traffic between all subnets in the local network
- You can add, remove, and modify routes in the main route table.
- The main route table is used implicitly by subnets that do not have an explicit route table association like a Custom route table.
####  Custom route table
- Each custom route table that you create will have the local route already inside it, allowing communication to flow between all resources and subnets inside the VPC. 
- You can protect your VPC by explicitly associating each new subnet with a custom route table and leaving the main route table in its original default state.
- If you want allow internet access (make public a subnet) you must to create the rule in the route table from the subnet to internet gateway (IGW)
- This type of routes can be defined in the Route rable: IGW (internet access for a Public subnet), NAT Gateway (internet access for a Private subnet), VPC Peering (Connect two VPCs), Virtual Private Gateway VGW (VPN or Direct Connectivity)
- Destination (IP where you want send traffic), Target (Service when the traffic is sent)

## Security
#### Access control list (ACL)
Think of a network access control list (network ACL) as a virtual firewall at the subnet level. 
Allow and deny type of rules are allowed to be defined in the ACL.
Network ACLs are considered stateless, so you need to include both the inbound and outbound ports used for the protocol
- Default network ACL: configured by default to allow incoming and outgoing traffic
- Custom network ACL
#### Security group
Security group is an instance level firewall that will allow traffic to reach the instance.
SG is not optional when an instance is created.
The default configuration of a security group blocks all inbound traffic and allows all outbound traffic. 
To allow inbound traffic, you must create inbound (only allow) rules.
A common design pattern is to organize resources into different groups and create security groups for each to control network communication between them.

![security_groups](/img/security_groups.jpg)

    Route tables to control outbound traffic mainly and Security (ACL and Security Group) to control how traffic ingress to vpc

## Gateways
#### Internet gateway
To activate internet connectivity for your VPC, you must create an internet gateway to connect your VPC to the internet.
NAT translates private IP addresses to public IP addresses, ensuring communication out to the internet.
#### Virtual private gateway
A virtual private gateway connects your VPC to another private network.
When you have both gateways, you can then establish an encrypted virtual private network (VPN) connection between the two sides.
#### Transit Gateway
Manage and simplify connections and peering for your Amazon VPCs

## Monitor
#### Amazon VPC Flow Logs
#### VPC Traffic Mirroring
#### Amazon CloudWatch

## Connectivity
AWS provides services and hybrid connectivity solutions to link your on premises and AWS networks.
#### AWS Transit Gateway
Manage and simplify connections and peering for your Amazon VPCs
#### AWS Cloud WAN
Connections between on premise network and AWS VPC
#### AWS PrivateLink
Establish secure and private connectivity between Amazon VPCs, AWS services within your region or inside another Amazon VPC, and your on premise network. 
#### AWS Client VPN
Connect remote team access to AWS and on premises resources.
#### AWS Site-to-Site VPN
Connect on premise with AWS VPC
#### AWS Direct Connect
To establish a secure physical connection between your on-premises data center and your Amazon VPC, you can use AWS Direct Connect.

## Edge Networking
On AWS, edge networking services securely transmit your user-facing data with improved latency globally. When you use the AWS edge networking services, your traffic moves off the internet and behind the AWS global network. AWS edge networking services sit at the AWS global edge locations and are configured to connect and deliver data with single-digit millisecond AWS network latency.
#### Amazon CloudFront
CDN
#### Amazon Route53
DNS
#### AWS Global Accelerator
Optimizes user traffic, from the user to the application.
#### AWS Shield Standard
Defends traffic from DDoS and malicious web attacks
#### AWS WAF
Application protection by using rules.

## Application Networking
work together to solve your application networking needs.
#### Amazon API Gateway
Creates, mantain and secures APIs at any scale
#### AWS App Mesh
Connect containers and microservices with application-level networking
#### AWS Cloud Map
Discover access to the most recent resources and services
#### Elastic Load Balancing

## Network Security
AWS provides your network and application security teams with services that address their particular protection needs and compliance requirements.
- Protect your environment.
- Inspect and filter traffic to prevent unauthorized access.
- Enforce fine-grained security policies at every network control point across your organization.
- Meet compliance requirements.

#### AWS Firewall manager
Centralize the way of manage and configure the firewall fules
#### AWS Shield
Defends traffic from DDoS and malicious web attacks
#### AWS WAF
Protects WebApps from common web exploits
#### AWS Network Firewall
Set up network security acces at VPC-level
