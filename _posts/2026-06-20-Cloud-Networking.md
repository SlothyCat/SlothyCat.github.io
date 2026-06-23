---
title: "Cloud Networking"
date: 2026-06-20 20:00:00 +0800
categories: [AWS Cloud]
tags: [AWS Cloud]
image:
    path: assets/images/cloud_network.jpg
    alt: Cloud Networking
---

# Introduction to networking
Let us see what cloud networking looks like! 

There's another AWS product that can help us control network access: `Amazon Virtual Private Cloud` (VPC).

### Internet Gateway and Virtual Private Gateways
#### Amazon VPC
It allows you to provision a logically isolated section of AWS Cloud where you can launch AWS resources in a virtual network that you define. They use the subnet to separate publicly accessible from private resources.

VPC can contain multiple pairs of public and private subnets for different availability zones.

**Key Benefits**:
1. Increase Security
2. Save Time
3. Control Environment

To allow public traffic to access the VPC. You will attach an internet gateway to the VPC. A door!

#### Virtual Private Gateways
If VPC only contains **private** resources, we can make use of a **Virtual Private Network (VPN)** to create a secure tunnel through the internet with encryption. With a virtual private gateway, we can establish a VPN connection between the VPC and another private network. 

>Virtual Private Gateways only allow traffic into the VPC if it comes from an approved network
{: .prompt-tip}


### More ways to connect to the cloud
There are 4 ways:
1. AWS Client VPN
2. AWS Site-to-Site VPN
3. AWS Private Link
4. AWS Direct Connect

#### AWS Client VPN
More for **remote** workers accessing on-premise networks. This is scalable as well and fully managed. It uses an OpenVPN-based client and works with global regions using the AWS global network.

>OpenVPN refers to the open source tunnelling protocol used to create secure, point-to-point connections
{:. prompt-info}

#### AWS Site-to-Site VPN
Connects securely **between on-premise networks** like data centres or branch offices. This is highly available, secure, fast and has private sessions.


#### AWS Private Link
Provides flexibility to privately connect to resources in other cloud providers as though they were in their own VPC. This gives high availability with simplified management rules. Can think of it as it used to **connect between VPCs**.

#### AWS Direct Connect
**Dedicated** private connection between your network and VPC in the AWS Cloud for **increased bandwidth**. This is useful for latency-sensitive applications, large-scale data migration and hybrid cloud architectures.

### Other Gateways
- **AWS Transit Gateway**
	- Connect VPCs and the on-prem network in a central hub
- **NAT Gateway**
	- for a private subnet, NAT service
- **API Gateway**
	- AWS service for creating, publishing, maintaining, monitoring and securing APIs to scale.


### Security Groups and Network ACL
ACL works the same way as I remember, but now there are security groups. Each EC2 instance belongs to its own security group, and it denies all traffic by default. You select what can enter or exit (**Allow** type rules). Network ACL has both **allow and deny** type rules

Security groups have **stateful** packet filtering, while network ACL is **stateless** packet filtering. Return traffic is automatically allowed for security groups as it **remembers the state**, but the network ACL will still check regardless.

ACLs are normally for the traffic in and out of subsets, while security groups are for individual EC2 instances.

> Network ACLs and Security Groups are the clients' responsibilities
{: .prompt-warning}


### Sequence for Configuring VPC
1. Create the Amazon VPC and specify the region
2. Create subnets (best to be across 2 AZs for high availability)
3. Create an Internet Gateway and Route traffic
4. Implement Network ACLs and Security Groups


### Global Networking
Remember our DNS? There is `AWS Route 53`, which is a DNS that works the same way as I remember, and it can route users to infrastructure outside of AWS, so no worries.

There is also `AWS Global Accelerator`, basically a **faster connection and more reliable**, but of course, more expensive.  It does this by providing static IP addresses, directing traffic over the AWS global network, and routing to optimal endpoints based on health, user location, and policies.

#### Delivering to global users
Companies can make use of `Amazon CloudFront` to distribute data and `Route53` to direct users'  requests.

**The Flow:**
User tries to access the company website, request is sent to Route 53. Route 53 uses a routing policy to find the closest region and send the request to the appropriate CloudFront edge location. Edge location picks up content from the designated origin server in the chosen region. 

# Summary
I learned more about what AWS has to offer for the networking experience between the cloud and users or other clouds over here. Some concepts that I have learned before now have a clearer product in my mind, for example, how the network looks like with the VPC.

![alt](/assets/images/pikachu_facing_the_wall.jpeg)
Air drying pi...