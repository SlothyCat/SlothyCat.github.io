---
title: "Introduction to Cloud"
date: 2026-06-14 23:00:00 +0800
categories: [AWS Cloud]
tags: [AWS Cloud]
image:
    path: assets/images/intro_to_cloud.svg
    alt: Introduction to Cloud
---

# Introduction to the Cloud
Let us finally learn about the cloud. I have always heard about cloud this cloud that, and I have actually never really learned about it before. I hope that this experience with AWS Cloud Practitioner Essential can help me understand it. Hopefully, I can understand well enough and be able to explain it to another non-technical friend!


### The AWS Cloud
#### Client-Server Model
With a Coffee Shop analogy. The customer makes a `request`, and the server with permissions `respond`s to the request. You only pay for how much you use. On-premise data centres will have the issue of capacity planning. Only need to set the right configuration to de-provision when extra computation power is no longer needed.


#### Cloud Computing
It refers to the **On-Demand delivery of IT resources** over the internet with **pay-as-you-go** pricing. 

**Its key benefits are covered in the video:**
1. Trade fixed expenses for Variable expenses 
2. Benefit from massive economies of scale
3. Stop guessing capacity
4. Increase speed and agility to try new things
5. Stop spending money running and maintaining data centres
6. Go global in minutes

>Because everything is so customisable and quick commission and decommission, there is `flexibility` in the business to focus more on the clients.
{: .prompt-tip}

#### AWS Global Infrastructure
**High Availability** makes sure your applications stay accessible with minimal downtime. Even if one component fails, the other can pick up the slack to keep the services running.

**Fault tolerance helps to design a system to continue to operate even if multiple components fail. Building resilience into every layer so that one fault will not bring down the whole system.

AWS operates in `Regions` that are located in various parts of the world. Within each region, there are 3 or more Availability Zones for redundancy. They are far enough not to be impacted by the same natural disaster. Within each AZ, there is at least one discrete data centre with redundant power, networking and connectivity.

#### AWS Shared Responsibility Model
Both the client and AWS are responsible for the security.

![Alt text](/assets/images/AWS_shared_responsibility_model.png)
Screenshot from the free learning materials in AWS's Cloud Practitioner Essential course.

Example mentioned: Client is responsible for applying security patches to the OS, as AWS does not have access to it.

### Cloud in Real Life
Since latency is important, we should choose the right AWS Regions. It is easier for us to reach a global audience with the cloud. To ensure that the company adheres to security regulations, we have to keep in mind the AWS Shared Responsibility Model to defend ourselves.


# Conclusion
I think everything that I previously knew about the cloud is all here. Some knowledge came from Security+, while some came from random reels, hehe. Looking forward to what I can learn in the upcoming modules! 

![alt](/assets/images/plane_cloud.jpeg)
Cloud shall not be only something floating in the sky!