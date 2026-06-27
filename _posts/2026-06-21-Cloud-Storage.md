---
title: "Cloud Storage"
date: 2026-06-20 20:00:00 +0800
categories: [AWS Cloud]
tags: [AWS Cloud]
image:
    path: assets/images/cloud_storage.jpg
    alt: Cloud Storage
---

# Introduction to Storage
There are multiple ways to store things in Amazon, and here are the 3 ways:
- Block Storage: persistent, low-latency blocks that can be encrypted
	- `EC2 instance store`: unmanaged, non-persistent, high-performance for temporary data
	- `Elastic Block Store (EBS`): a managed service that is persistent
- Object Storage: Unlimited scalability with data as objects in a flat address space
	- `Simple Storage Service (S3)`: Fully managed, scalable object storage service
- File Storage: provide shared file systems accessible over the network so multiple users can access the same data at the same time (sounds like SharePoint)
	- `Elastic File System (EFS)`: Fully managed, scalable NFS (Network File System) access to files over the network)
	- `FSx`: Fully managed file storage service for popular file systems like Windows

Other storage services, like Storage Gateway, provide on-prem access to virtually unlimited cloud storage and `Elastic Disaster Recovery`.

### EC2 Instance Store and EBS
EC2 Instance Store **does not have data persistence**, and data will be lost when the instance is stopped or terminated. This is where EBS comes in. **EBS is persistent**, and it has a variety of different volume sizes and types. EBS can be easily replicated to achieve high availability.

However, the EC2 instance store is **automatically included** with many EC2 instances and is both cost-effective and High-Performance.

>Amazon EBS volumes exist independently from the instance and persist even after the instance is terminated.
{: .prompt-tip}

#### EBS data lifecycle
**EBS snapshots** are point-in-time backups of the EBS volumes. It is incremental, meaning that they only capture recent changes compared to the previous snapshot. 

The Amazon Data Lifecycle Manager automates the schedule snapshots by allowing you to define custom EBS snapshot policies.

### Amazon Simple Storage Device S3
It is a **fully managed, highly available** object storage service for storing and retrieving any amount of data as objects. It offers **99.999999999 percent durability**, meaning your data is highly protected against loss.

It stores files as objects in containers known as buckets.

Each object typically includes the _data_ itself, _metadata_, and a unique identifier, or _key_. The key is essentially the file name.

Buckets have a **globally unique name** across all of AWS. Buckets can be configured with various settings like versioning, logging and access permissions.

S3 maintains security through: Bucket Policies, Identity-Based Policies and Encryption

#### S3 Intelligent Tiering
Splits into: Frequent access, infrequent access and archive instant access tiers. Cheaper when things are not accessed that frequently. 

| Name                                     | Description                                                                                                                                 |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| Standard                                 | general-purpose storage (default)                                                                                                           |
| Standard Infrequent Access               | accessed less frequently but requires rapid access when needed                                                                              |
| One Zone Infrequent Access (One Zone-IA) | stores data in a single Availability Zone, reducing costs compared to S3 Standard-IA, which uses three zones.                               |
| Express One Zone                         | stores data in a single Availability Zone, delivers data access speed up to 10x faster and request costs up to 80% lower than S3 Standard.  |
| Glacier Instant Retrieval                | archiving data that is rarely accessed and requires millisecond retrieval                                                                   |
| Glacier Flexible Retrieval               | offers low-cost storage for archived data that is accessed 1–2 times per year.                                                              |
| Glacier Deep Archive                     | Archive storage class has a default retrieval time of 12 hours. It is designed for customers that retain data sets for 7–10 years or longer |

We can also set up transition actions and expiration actions:
- **Transition actions:** define when objects should transition to another storage class.
- **Expiration actions:** define when objects expire and should be permanently deleted.

### Elastic File System (EFS)
It is fully managed, scalable and operates using the Linux Network File System protocol. Its benefits include:
1. Multi-AZ redundancy
2. Shared Access
3. Elastic Storage

There are different storage classes, too

| Type of Storage Class | Description                                                                                                   |
| --------------------- | ------------------------------------------------------------------------------------------------------------- |
| Standard              | Multi-AZ resilience and the highest levels of durability and availability                                     |
| One Zone              | additional savings by saving your data in a single place                                                      |
| Archive               | accessed only a few times a year or less and that does not need the sub-millisecond latencies of EFS Standard |

>By default, for transitions, files are not moved back to Standard storage, and they remain in the IA or Archive storage class when they are accessed.
{: .prompt-tip}


### FSx
It supports multiple file system protocols like **Windows File Server**, **NetApp ONTAP**, **OpenZFS** and **Lustre**. It is also managed, scalable and cost-effective.

Not much is really mentioned about this, but I guess it follows the standard, one zone and archive way too?

### AWS Storage Gateway
It is a hybrid cloud storage service that makes it possible to seamlessly integrate on-premises environments with AWS Cloud storage. Think of it as cache in on-prem and local storage extended to the cloud.

Benefits:
1. Seamless integration
2. Improved data management
3. Local caching
4. Cost optimisation - compared to fully on-prem  

#### Types of Gateways
- **S3 File Gateway** (in files)
	- bridges your local environment with Amazon S3
	- It appears to your local systems as a standard file server
	- Files written to this server are automatically uploaded to Amazon S3
- **Volume Gateway** (as a whole ass volume - containers)
	- bridge between your on-premises infrastructure and AWS Cloud storage by presenting your cloud data as iSCSI volumes that can be mounted by your existing applications.
	- _Cached volume mode_ stores primary data in the cloud, while frequently accessed data is cached locally for low-latency access
	- _Stored volume mode_ locally keeps your complete dataset while asynchronously backing it up to the cloud as EBS snapshots.
- **Tape Gateway** (as a virtual tape)
	- provides an interface that works with existing tape backup software, making the transition from physical tapes to cloud storage seamless.


### Elastic Disaster Recovery
Okay, let us look at the solution for Disaster Recovery. NGL, there are so many services I'm about to explode. 🤯

The clients' servers' block-level data is continuously replicated to AWS, making it ideal for uses that require robust disaster recovery solutions. It supports both physical and virtual servers to enable rapid recovery during disruptions.

This is separate from the multiple AZ approach.

# Summary
Learned more about the various storage options and methods that AWS has to offer here. I used to think that data is just stored in the cloud, but now I know that, based on the different types of data and frequency of use, there will be a more suitable method of storage!

![alt](/assets/images/blue_cats_store.jpeg)
Some cats to heal up~
