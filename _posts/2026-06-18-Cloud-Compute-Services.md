---
title: "Cloud Compute Services"
date: 2026-06-18 20:00:00 +0800
categories: [AWS Cloud]
tags: [AWS Cloud]
image:
    path: assets/images/cloud_compute_services.jpg
    alt: Cloud Compute Services
---

# Introduction
We will learn more about other services that help support cloud computing in AWS.

### Introduction to Serverless Computing
Before we go into **serverless**, we have learned in the previous module about the scope of responsibility for **unmanaged** services. **Managed** services basically means that AWS has responsibility over the OS, network and firewall configuration as well as the platform and application management.

Managed Services reduce the number of infrastructures you have to manage!

#### Fully-managed services
This is one step above Managed Services, and this is also known as serverless. This eliminates the need to provision any servers at all, as the underlying infrastructure is fully managed by AWS.

Serverless covers the network traffic protection and server-side encryption, which is not covered by Managed Services.

![alt](/assets/images/AWS_compute_services_responsibility_matrix.png)


### AWS Lambda
It is a serverless compute service that runs code in response to events without the need to provision or manage servers. It is also known as Function-As-A-Service.

#### Procedure:
1. Upload your code to Lambda (your named function, does not have to be a lambda function)
2. Set code to trigger from an event source (AWS service, mobile app or HTTP requests)
3. Run code when triggered
4. Pay only for the compute time used

>Maximum time for a lambda function is 15minutes, so if the code cannot be split into a 15-minute segment, `AWS Lambda` will not be a good choice.
{: .prompt-warning}


### Containers and Orchestration on AWS
Over here, we are introduced to the **AWS Containers solution** that packages everything the application needs to run so that it works the same on any computer. This is also good for deployment consistency with containers. 

#### AWS Fargate
It is a **serverless** compute engine for containers

#### AWS Orchestration Services
`Amazon Elastic Container Service (ECS)` is a scalable container orchestration service for running and managing containers on AWS.

It pairs with:
- EC2: small to medium businesses that need full control over infrastructure or a custom application
- Fargate: perfect for startups that have variable traffic and no server management required


`Amazon Elastic Kubernetes Service (Amazon EKS)` is a fully managed service for running Kubernetes on AWS.

It pairs with:
- EC2: best for enterprises and allows deep customisation of EC2 with Kubernetes scalability, ideal for complex, large-scale workloads
- Fargate: for teams who want Kubernetes flexibility without managing servers

#### AWS Container
`Amazon Elastic Container Registry (ECR)` is where you store, manage and deploy container images. It supports container images that follow the Open Container Initiative.


#### Linking it all together...
ECR is a registry that has all the container images we uploaded, then the orchestrator pulls them and compute it with the chosen compute pair.


### Other computer services covered...

| Name                  | Description                                                                                                  |
| --------------------- | ------------------------------------------------------------------------------------------------------------ |
| **Elastic Beanstalk** | fully managed service that streamlines the deployment, management, and scaling of web applications           |
| **Batch**             | fully managed service that you can use to run batch computing workloads on AWS                               |
| **Lightsail**         | cloud service offering virtual private servers (VPSs), good for small projects                               |
| **Outposts**          | fully managed hybrid cloud solution that extends AWS infrastructure and services to on-premises data centres |

# Summary
This module felt more like a massive info dump covering a lot of services. I mean, great that they kept the others quite short so it plants a seed now and maybe I will see more of them later!

This module covers more on the various service types: Managed, Unmanaged and Serverless, as well as the containerisation solutions AWS has.

![alt](/assets/images/homemade_chicken.jpeg)
This is a homemade fried chiki by my floormate from Austria!
