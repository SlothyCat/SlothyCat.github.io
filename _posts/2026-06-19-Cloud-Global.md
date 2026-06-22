---
title: "Cloud Global"
date: 2026-06-19 20:00:00 +0800
categories: [AWS Cloud]
tags: [AWS Cloud]
image:
    path: assets/images/global.jpg
    alt: Cloud Global
---

# Introduction
We have previously gone through quickly about AWS Global Infrastructure, and we will learn more about it now!

This helps businesses to scale consistently, ensuring that the global users have a similar user experience!

We will start by considering which region or set of regions to host our real-life resources. AWS has smaller footprint facilities called **edge locations**. They **cache items** so that users can access the content they need with low latency!

We also make use of `CloudFormation` to automate the deployment of cloud resources. These services use IaC, Infrastructure as Code (learned in Security+), to scale consistently and reliably.

### Choosing AWS Regions
There are mainly 4 key considerations when we choose which region to host our cloud resources.

#### Compliance
There might be **regulations and requirements** that the company must follow, such as the GDPR for the EU. Sometimes data has to stay within certain geolocations.

#### Proximity
As we want to reduce the **latency** for our users, we should make use of regions close to the user base to minimise data travel time.

#### Feature Availablity
Since AWS is always pushing out **new services and features**, not all the regions will have them due to either keeping a small rollout to observe or due to compliance and security requirements.

#### Pricing
**Operational cost** can impact the overall expense to host applications and services. Tax also affects the pricing!


### Diving deeper into AWS Global infrastructure
As we have learned previously about how AWS AZs can keep a high availability with multi-AZ deployment, we also know that there are **edge locations**. These edge locations are strategically placed to provide low-latency access to AWS services and content delivery.

#### Edge Locations
They provide **multiple services** to run closer to users, such as the `Amazon CloudFront` networking service. `CloudFront` is a content delivery network (CDN) and has a caching system.


> Regions have multiple isolated Availability Zones (at least 3) and each zone has its own power, networking and connectivity. Each AZ has at least 1 data centre. **Edge locations are located outside of AWS Regions** and cache frequently accessed content.
{: .prompt-tip}


### Infrastructure and Automation
As we know (what I learned in Security+), we can make use of Infrastructure as Code to ensure consistent and fast setup in the cloud. 

#### AWS CloudFormation
This is an **IaC** service that we can use to define the AWS resources in a **declarative** way using text-based documents called `CloudFormation templates`. We do not need to specify how to build it as the service will take care of provisioning and configuring those resources for you.


#### Interacting with AWS resources
Previously, we mentioned 3 ways: **AWS Management Console** (Web, good for new users), CLI and SDK. We consider CLI and SDK to be under **programmatic access**. 

AWS CloudFormation falls under **Infrastructure as Code**, as it automates resource management by offering efficient and repeatable resource creation and management.


# Summary
I have learned more about the AWS global infrastructure, like the AWS region, Availability Zones and Edge Locations. I have also learned about the AWS IaC service CloudFormation. This provides slight clarity in the different deployment environments, and there are also services to help us do it consistently.

![alt](/assets/images/sleeping_cinna.jpeg)
Eepy Cinna!