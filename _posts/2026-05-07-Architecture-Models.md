---
title: "3.1 Architecture Models"
date: 2026-05-07 18:15:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/architecture.jpg
  alt: Architecture Models
---

# Introduction to Architecture Models including Cloud!
Oh em gee! I am finally seeing the cloud. Okay, but I think I'm not knowledgeable at all in this. Cloud is just the thing that floats around in the sky and looks soft to me. But let us see what we can do about cloud security. I want to do a `AWS cloud practioner` after this to learn more about it!

## Cloud Security Concepts
Cloud deployments include **IaaS, PaaS and SaaS** that distribute responsibility between provider and customer via a shared responsibility matrix. 

#### Hybrid & Multi Cloud challenges
Using multiple cloud providers would mean that there is **more flexibility**, but also **more security overhead**. Since there is no direct communication, there might be mismatch risk, configuration differences or log format differences that will make it risky. Also, data is transmitted in the open between the 2 cloud.

#### Third-Party Cloud Components
We will also work with **in-house app**s and also **third party firewalls**. We also need to manage risk for all 3rd party technologies and monitor their systems for security and availability.

#### Infrastructure as Code (IaC)
Apparently, rather than configuring hardware manually, you can **define the whole infrastructure using code** that specifies the hosts, web servers, database servers and their configurations. This makes it very easy to modify and redeploy without touching the physical hardware.

#### Serverless Architecture
Sometimes, the application is broken into **small, discrete functions** that run only when called. This makes sure that only the necessary parts are used, and that the cloud will be responsible for the safety.

#### Microservices vs Monolithic Architecture

| Property    | Monolithic                                | Microservices                                                 |
| ----------- | ----------------------------------------- | ------------------------------------------------------------- |
| Structure   | Single large executable                   | Many small independent services                               |
| Deployment  | Entire app is re-deployed for any changes | Individual services updated independently                     |
| Scalability | Scale the whole app                       | Scale only the overloaded service                             |
| Resilience  | One failure can crash everything          | Other services continue if one fails                          |
| Security    | One security posture for everything       | Security scoped per service (e.g. auth service vs DB service) |
| Interface   | Direct                                    | Via API gateway                                               |


## Network Segmentation & SDN
Once again, we have the physical segmentation and logical segmentation via VLANs.

#### SDN - Planes of Operation
Software-Defined Networking breaks the network device into 3 planes
- **Data**: Actual movement of packets
- **Control**: Tell the data plane where to send the traffic
- **Management**: dictates how Control and Data will behave

#### SDN in the cloud
Cloud infrastructure can also spin up network devices on demand. A bit unclear on this for now, but I am assuming that the SDN can work well with cloud since we can just say we want this and that with the IaC property.


## Other Infrastructure Concepts
Organisations can choose between on-premise and cloud infrastructure, each with its own pros and cons.

|Factor|On-Premises|Cloud|
|---|---|---|
|Control|Full — you own all decisions|Limited — provider controls underlying infrastructure|
|Cost|High — hardware, staffing, cooling|Lower upfront — pay-as-you-go|
|Staff|Dedicated in-house IT/security team|Provider handles much of the security|
|Changes|Immediate — no third party needed|May require provider involvement|
|New equipment|Slow — purchase, configure, install|Fast — spin up on demand|
|Security centralisation|Local|Centralised with other cloud services|

#### Centralised vs Decentralised Management
Most organisations are decentralised by default, and they need a **Centralised Management Console**. This allows them to have consolidated alerts and logs, easier global patches and unified visibility. However, it is not scalable, and it is a single point of failure.

#### Virtualisation vs Containerisation
VMs and Containers like Docker. **VMs have their own full guest OS** while **containers share the same host OS**. VM is more isolated compared to a container, but is less efficient.

#### IoT
These are networked devices used for automation and convenience. It is a security concern as these are usually designed without any security considerations.

#### SCADA/ICS
**Supervisory Control and Data Acquisition**, also known as an **Industrial Control System**. This is used mainly in things like manufacturing, power generation, oil refineries and water treatment. It must be completely segmented from the external network, as the resources are very important at the national level.

#### Real-Time Operating System (RTOS)
This is a **deterministic OS** where one process can take full priority over all system resources when needed. It is built for time-sensitive tasks. These are self-contained and access-restricted by design and cannot install traditional Anti-virus

#### Embedded Systems
Hardware and software that are built together to be a **self-contained, single-purpose device** to do only one thing. It is hard to breach, but if compromised, it is hard to fix as well.

#### High Availability
A bit random that it falls under here, but okay, there are just 2 things to take note of:
1. **Active/Active**: Both are always running together; if one fails, the others work harder
2. **Active/Passive**: Only one handling traffic, the other is the backup that will start working if the first fails
This is normally quite expensive to maintain.

## Infrastructure Considerations
This has all the different considerations that we have in the security architecture. A bunch of them.
1. Availability & Resilience Metrics - MTTR Mean Time to Repair
2. Cost Considerations
3. Responsiveness
4. Elasticity and Scalability
5. Orchestration (Automatically deploy)
6. Cybersecurity Insurance
7. Recovery Planning
8. Patching
9. Power Infrastructure (Uninterruptible Power Supply, UPS)
10. Computational power (Compute Engine


# Summary
This does not really tell me how the cloud works, but rather generic things to look out for in infrastructure. Feels very common sense when you look at them, but I guess I will only be able to go through each when it is listed down as a checklist, or it is easy to forget all these considerations!

![Alt Text](/assets/images/shanghai_nightview.jpeg)
My second time in Shanghai and also second time taking picture of this again!

