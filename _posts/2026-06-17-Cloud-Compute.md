---
title: "Introduction to Cloud Computing"
date: 2026-06-14 23:00:00 +0800
categories: [AWS Cloud]
tags: [AWS Cloud]
image:
    path: assets/images/cloud_computing.jpg
    alt: Introduction to Cloud Computing
---

# Introduction to Cloud Computing
Over here, we will learn more about how computational power is being offered as a service in the cloud. From what I know, it is about borrowing the hardware infrastructure to run deployables. 
### Introduction to Amazon EC2
For the computational part of Amazon, they offer `EC2` as the solution. Amazon EC2 is more **flexible**, **cost-effective**, and **faster than managing on-premises servers**. You will only pay for **running instances**, not for stopped or terminated ones.

**Its Characteristics:**
1. Pay only for the compute time used when an instance is running
2. Scale up or down based on demand
3. Stop using instances after a workload has completed
4. Provision and Launch an Amazon EC2 instance within minutes

We can make use of EC2 to launch, connect to and use virtual instances in the cloud. 

#### Step 1: Launch
We have to select an **Amazon Machine Image** (AMI) which defines the OS and might include additional software. You can also choose an instance type which determines the underlying hardware resources like CPU, memory and network performance.

#### Step 2: Connect
Applications can interact with services running on the instance over the **network**.

Users or Admins can connect via `SSH` for Linux instances or `RDP` for Windows instances. Alternatively, AWS services also provide **AWS Systems Manager** to provide a secure and simplified method for accessing instances.

#### Step 3: Use
After you connect, you can run commands, install software, add storage, organise files and perform other tasks.


>EC2 instances are **VMs**. AWS manages the **hypervisor** and isolates instances from each other; this concept is also known as **multi-tenancy**.
{: .prompt-tip}


### Amazon EC2 Instance Types
There are a total of 5 instance types meant for various uses. We should select the correct type based on our use case.

#### General Purpose
It provides a **balanced** mix of compute, memory and networking resources. Great for diverse workloads (web services, code repositories) and when workload performance is uncertain.

#### Compute Optimised
Ideal for **compute-intensive** tasks like gaming servers, high-performance computing (HPC), ML and scientific modelling.

#### Memory Optimised
Ideal for **memory-intensive** tasks like processing large datasets, data analytics and databases. They provide fast performance for memory-heavy workloads.

#### Accelerated Computing
Uses **hardware accelerators like GPUs** to efficiently handle tasks like floating point calculations, graphics processing and ML.

#### Storage Optimised
Designed for workloads that require **high performance for locally stored data**, such as large databases, data warehousing and I/O intensive applications.

>Naming Convention can be found [here][https://docs.aws.amazon.com/ec2/latest/instancetypes/instance-type-names.html]
{: .prompt-info}


### Provisioning AWS resources
It is provisioned using API calls, through:
1. AWS Management Console
2. AWS CLI
3. AWS SDK

#### AWS Management Console
This is the **web interface** that is easy to use and normally meant for new starters to learn! You can set up test environments, view bills, monitor resources and manage non-technical start. In other words, good for me 😊

#### AWS CLI
Directly from the **command line interface**. This is normally meant for automation by scripting actions.

#### AWS SDK
Allows **interaction through various programming languages**. AWS provides documentation and sample code. This is good for developers trying to integrate AWS services into their application using language-specific APIs.


#### Unmanaged Service
Amazon EC2 is an **unmanaged service** and requires the client to perform all of the necessary security configurations. AWS is only in charge of the software of the compute, storage, database and networking as well as the hardware.


### Amazon Machine Images
The **AMI includes OS, storage setup, architecture type, permissions for launching and extra software**. We can either custom-build ours, choose a pre-configured one or buy it from the AWS Marketplace.

The AMIs provide repeatability through a consistent environment for every new instance. Since the configurations are identical, this helps with scaling and reducing errors and managing large-scale environments.

### Amazon EC2 Pricing
There are multiple pricing options
1. **On-Demand** - Pay as you consume
2. **Reserved Instances** - Discount by committing 1/3 years using specific instance families and AWS regions
3. **Spot Instances** - Bid on spare compute capacity but can be interrupted
4. **Savings Plan** - Discount by committing 1/3 years by committing to a consistent usage level
5. **Dedicated Hosts** - Reserve an entire physical server for exclusive use. Best for security.
6. **Dedicated Instances** - Isolation from other customers and pay for instances running on hardware dedicated only to your account.

The key **difference** is that Dedicated Instances **provide isolation without you choosing which physical server** they run on. Dedicated Hosts give you an **entire physical server for exclusive use**, providing complete control over instance placement and resource allocation.

So I guess it could be sharing the same stack but still isolated.


### Scaling EC2
Scalability refers to the ability of a system to **handle an increased load by adding resources**. It is hard to do capacity planning, especially for new businesses, and this is where on-demand shines.

#### EC2 Auto Scaling
Amazon EC2 Auto Scaling automatically adjusts the number of EC2 instances based on changes in application demand, providing better availability. This happens with 2 approaches:
1. **Dynamic** - Real Time
2. **Predictive** - based on anticipated demand

This can be configured with 3 key settings:
1. Minimum Capacity
2. Desired Capacity (if not specified, defaults to minimum)
3. Maximum Capacity

There is also horizontal and vertical scaling that refers to more in parallel and stronger respectively!


### Directing Traffic with Elastic Load Balancing
Load balancers, something that I have learned in Security+ ehe. It takes in requests and loads them to instances. Elastic Load Balancing **automatically distributes incoming application traffic across multiple resources**. This decouples the infrastructure, and traffic gets distributed effectively.

#### Some Routing Methods mentioned:
1. Round Robin
2. Least Connection
3. IP hash
4. Least Response Time
Sounds like my OS concepts for concurrency... I mean technically we are doing concurrent work!


>It does not add any instances on its own!
{: .prompt-warning}


### Messaging and Queuing
2 Amazon products are being introduced here:

#### Amazon SQS:  Amazon Simple Queue Service
`SQS` enables you to send, store, and receive messages between software components at any volume. This is done without losing messages or requiring other message consumers to be available

#### Amazon SNS: Amazon Simple Notification Service
`SNS` messages are different from SQS messages because they require a response right now.


With a microservice approach, we can decouple our architecture. Amazon EventBridge is a serverless service that helps to connect services using events. These events are passed to the next service and this "pass" can be either `SQS` or `SNS`.


# Summary
I learned more about how to get Cloud Computing running in AWS, specifically here. There are a bunch of services to help businesses handle their computing in the cloud which is pretty cool since I never hosted anything on the cloud before with me configuring stuff!

![alt](/assets/images/pink_dino.jpeg)
Unpacking the mysteries of 'cloud' one by one!