---
title: "Cloud: The Ad Hoc Bits"
date: 2026-06-21 21:30:00 +0800
categories: [AWS Cloud]
tags: [AWS Cloud]
image:
    path: assets/images/cloud.jpg
    alt: Cloud
---

# Introduction to Monitoring, Compliance and Governance in AWS Cloud
To effectively monitor our AWS cloud solutions, we need to do the following:
1. Secure systems
2. Monitor systems
3. Conduct audits
4. Ensure compliance

### Introduction to Monitoring
Monitoring provides a way for you to **continuously observe and analyse** system activity, network traffic, and security events to detect potential threats or anomalies.

This helps us ensure the **security, availability, reliability, and performance** of cloud-based workloads and data.

#### Amazon CloudWatch
`CloudWatch` monitors your AWS resources and the applications that you run on AWS in real time. With `CloudWatch`, you gain **system-wide visibility into resource utilisation, application performance, and operational health**.

It contains:
- `CloudWatch metrics`
- `CloudWatch alarms`
- `CloudWatch dashboards`
- `CloudWatch logs`

#### AWS CloudTrail
This is a useful service for auditing. `CloudTrail` **tracks user activity and API usage** in the AWS Cloud, on premises, and even with other cloud providers. `CloudTrail` provides a detailed history of API calls, so you can track changes and identify who made them and when.

Similar to `CloudWatch`, `CloudTrail` also has a few features:
- **events**
	- actions performed within the AWS account such as API calls
	- immutable history of the past 90 days
- **logs**
	- delivered to `S3`
	- compliant with `PCI` and `HIPAA`
- **insights**

> By default, `CloudTrail` event history only retains the past 90 days. For longer retention, configure a trail to deliver your logs to `S3`.
{: .prompt-warning}

### Compliance tools for AWS
AWS helps you meet compliance goals and requirements in the following ways:
- **Inheriting the latest security controls** that AWS uses on its own infrastructure
- **Third-party validation** for thousands of global requirements
- **Streamlining and automating** compliance
- **On-demand** compliance reports

#### AWS Artifact
`AWS Artifact` provides **no-cost, on-demand access to AWS security and compliance reports** and select online agreements.

There are 2 types:
1. **Agreements**
	1. Review, accept, and manage agreements for an individual account
2. **Reports**
	1.  Provide compliance reports from third-party auditors.


#### AWS Compliance Portal
There is other useful documentation about compliance that can be found here, including:
- AWS answers key compliance questions
- An overview of AWS risk and compliance
- An auditing security checklist

#### Configuration guidelines

| Service               | Descriptions                                                                  |
| --------------------- | ----------------------------------------------------------------------------- |
| **AWS Config**        | to assess, audit, and evaluate the configurations of your AWS resources.      |
| **AWS Audit Manager** | continually audits your AWS usage to simplify risk and compliance assessment. |


#### AWS Organizations
**Centrally manage and govern** your environment as you grow and scale your AWS resources. It helps you manage policies for groups of accounts and automate account creation.

There are different terminologies and concepts covered in `AWS Organizations`:

| Term                               | Descriptions                                                                                                                                        |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Management Account**             | The management account is the central AWS account that creates and manages the organisation. It's responsible for overall control and governance.   |
| **Organisational Unit (OU)**       | logical grouping of accounts in an AWS Organization.                                                                                                |
| **Service Control Policies (SCP)** | policy that lets you place restrictions on the AWS services, resources, and individual API actions that users and roles in each account can access. |
| **Member Account**                 | a member account that has unique requirements that do not overlap with those of an organisational unit.                                             |

### Governance
AWS services that can help govern and enforce services and accounts to meet your company's requirements:

| Service                 | Descriptions                                                                                                                                                                             |
| ----------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **AWS Control Tower**   | enforce and manage governance rules for security, operations, and compliance at scale across all your organisations and accounts in the AWS Cloud.                                       |
| **AWS Service Catalog** | create, share, and organise from a curated catalogue of AWS resources. You can deploy baseline networking resources and security tools for new AWS accounts so you can govern consistently |
| **AWS License Manager** | manage your software licences and fine-tune your licensing costs.                                                                                                                        |


### AWS Health
`AWS Health` is the go-to data source for events and changes affecting the health of your AWS Cloud resources. It notifies you about service events, planned changes, and account notifications to help you manage and take action.

> But what is "health"? Think of it as a yes or no on whether one component is responsive and functioning.
{: .prompt-tip}

| Service                  | Descriptions                                                               |
| ------------------------ | -------------------------------------------------------------------------- |
| **AWS Health Dashboard** | view account-specific health information and get AWS Health event updates. |

### Other services

| Service                 | Descriptions                                                                                                                                                                                                       |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Trusted Advisor**     | continuously evaluate your AWS environment by using best practice checks across several categories. Helps you align with AWS best practices, prioritise recommendations, and optimise your AWS resources at scale. |
| **IAM Access Analyzer** | provides capabilities to set, verify, and refine permissions by analysing external access and validating that your policies match your corporate security standards.                                               |

# Introduction to Pricing and Support
Now that we have gone through so many services, how much do we have to pay, and what kind of support do we receive after purchasing them?

### AWS Pricing Concepts
As we know, AWS has been pushing the idea that they do auto-scaling and everything is pay on demand. So here are the actual key concepts that they use:
1. Pay as you go
2. Save when you commit (long term plans)
3. Pay less by using more (tiered pricing)

There are 3 fundamental driving factors of cost for AWS, which are Compute, Storage, and Outbound Data Transfer.

> Others include: service category or type, configuration, AWS Region, and which pricing model you choose
{: .prompt-info}

### AWS Pricing and Billing Service
As we recall, we were handed the `AWS Organizations` service to provide centralised management and governance of the AWS environment — turns out it can also consolidate billing here too!

Other services include:


| Service                                       | Descriptions                                                                                                                                                                                    |
| --------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **AWS Billing and Cost Management dashboard** | centralises cost management, showing current charges, usage, forecasts, and detailed breakdowns                                                                                                 |
| **AWS Budgets**                               | set custom budgets and send alerts when costs, usage, or Savings Plans and Reserved Instances (RIs) utilisation or coverage exceed defined thresholds.                                          |
| **AWS Cost Explorer**                         | visualise, analyse, and manage AWS costs and usage with interactive graphs, reports, and forecasts. It provides insights into spending patterns, trends, and Reserved Instance recommendations. |
| **AWS Pricing Calculator**                    | web-based planning tool that you can use to create estimates.                                                                                                                                   |

### AWS Support Plans
There are multiple types of support given for AWS clients.

![AWS support plans](/assets/images/AWS_support_plans.png)

There are also other sources that we can get useful resources from:
1. AWS re:Post
2. AWS Trust and Safety Center
3. AWS Solutions Architects
4. AWS Professional Services
5. Self-Support at AWS

### AWS Marketplace
The `AWS Marketplace` is a digital catalogue that includes thousands of software listings from independent software vendors. The solutions offered in the catalogue include SaaS, ML, AI, data, and analytics.

### AWS Partner Network
It is a global community that uses AWS technologies, programmes, expertise, and tools to build solutions and services for customers.

> I think we can think of partners as experienced craftsmen who make use of AWS tools — you can consult them for specialised solutions!
{: .prompt-tip}

### Cost Optimisation
Capacity Planning is kinda always the issue, so AWS has some services to cater for each type of resource:
- Compute instances - AWS Compute Optimizer / AWS Auto Scaling
- Storage: pick the correct Storage class
- Relational Database - Relational Database Service


# Migrating to AWS Cloud
So what if we already have our own stuff, how do we migrate over to AWS Cloud?

### Three phases of migration
1. Assess
	1. build business case for migration and assess readiness
2. Mobilise
	1. mobilise resources needed for migration
3. Migrate and Modernise
	1. use strategy plan and best practices

### AWS Cloud Adoption Framework
The framework provides tools to help accelerate the migration journey, organise resources, and align management during the transition.

**Benefits**:
- Reduce business risk
- Improve sustainability and corporate transparency

#### 6 Aspects of AWS CAF

| Aspect     | Description                                                                                                                                                                        |
| ---------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Business   | IT aligns with business needs and IT investments will link to key business results                                                                                                 |
| People     | Evaluate the human resources to restructure roles for the new cloud deployment and provide training if needed                                                                      |
| Governance | Understand how to update the staff skills and processes necessary to maintain business governance in the cloud. Manage and measure cloud investments to evaluate business outcomes |
| Platform   | Principles and patterns for the architecture model                                                                                                                                 |
| Security   | Meets security objectives for visibility, auditability, control and agility                                                                                                        |
| Operations | day-to-day run, use, operate and recover IT workloads to normal levels and identify any training required                                                                          |

### 7 Migration Strategies
1. Relocate: change hosting location to cloud
2. Rehost: lift and shift, move applications without changes
3. Replatform: lift, tinker and shift, make a few cloud optimisations to realise tangible benefits
4. Refactor: re-architecting, usually driven by strong business needs
5. Repurchase: moving from traditional licence to SaaS
6. Retain: keep applications critical for the business in the source environment
7. Retire: remove applications that are no longer needed

### Migration Services and Tools


| Service                           | Descriptions                                                                                             |
| --------------------------------- | -------------------------------------------------------------------------------------------------------- |
| **Migration Evaluator**           | migration assessment service that helps you create a business case for AWS Cloud planning and migration. |
| **Application Discovery Service** | discovers on-premises server inventory and connections.                                                  |
| **Migration Hub**                 | centralised hub to take you from discovery, assessment, planning, and execution of your migration.       |
| **Application Migration Service** | tool to move and improve your on-premises and cloud-based applications.                                  |

Beyond these services, there are also AWS Migration and Modernisation Competency Partners to help with migrating to the cloud.

### Database Migration
Migrating your database to the cloud can provide an opportunity to redesign and improve your database architecture. We will have to consider both homogeneous and heterogeneous migrations (referring to the type of database).


| Service                                | Descriptions                                                                                                                 |
| -------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| **AWS Database Migration Service DMS** | quickly and securely migrate databases and perform ongoing data replication tasks for live databases and data warehouses.    |
| **AWS Schema Conversion Tool SCT**     | convert database schemas and code objects (like stored procedures, views, and functions) from one database engine to another |

#### Transferring Data Online

| Service                 | Descriptions                                                                                                             |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------ |
| **AWS DataSync**        | designed for automating and accelerating data transfer. DataSync simplifies and accelerates moving large amounts of data |
| **AWS Transfer Family** | seamlessly manage and share data with simple, secure, and scalable file transfers.                                       |
| **Direct Connect**      | establish a dedicated private connection between your network and virtual private cloud (VPC) in the AWS Cloud.          |

#### Transferring Data Offline
**Snowball Edge Storage Optimized devices**: These devices deliver high-performance NVMe storage, making it possible to simplify multi-petabyte data migrations from on-premises locations to AWS.

> Offline transfer is meant for when moving data over the network would be too slow or impractical — think petabytes rather than gigabytes.
{: .prompt-info}

# Introduction to Well-Architected Solutions

### AWS Specialised Services
Normally split into 4 types:
1. Development 
2. Business Application 
3. End-user computing
4. IoT

#### Development

| Service              | Descriptions                                                                                                                                                                   |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **AWS CodeBuild**    | fully managed continuous integration service that compiles source code, runs tests, and produces software packages for deployment.                                             |
| **AWS CodePipeline** | fully managed CI/CD service that automates the build, test, and deploy phases of your release process                                                                          |
| **AWS X-Ray**        | powerful tracing, debugging, and performance analysis tool that helps developers visualise application behaviour.                                                               |
| **AWS AppSync**      | fully managed GraphQL service. With AWS AppSync, developers can create a single GraphQL API that can securely access, manipulate, and combine data from multiple data sources. |
| **AWS Amplify**      | streamline the process of developing, deploying, and managing secure and scalable full-stack applications on AWS.                                                              |

#### Business Application

| Service                                      | Descriptions                                                                                                                                                                   |
| -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon Connect**                           | efficiently set up and operate a scalable customer service call centre.                                                                                                        |
| **Amazon Simple Email Service (Amazon SES)** | scalable and cost-effective email service provider that can be integrated into any application for reliable, high-volume email automation.                                     |

#### End-User Computing

| Service                              | Descriptions                                                                                                                                                            |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon AppStream 2.0**             | fully managed service that streams applications from the cloud directly to any compatible device.                                                                       |
| **Amazon WorkSpaces**                | fully managed cloud-based desktop computing service. With WorkSpaces, employees can securely access their work environment from any device with an internet connection. |
| **Amazon WorkSpaces Secure Browser** | fully managed remote enterprise browser. It provides a protected environment for employees to access private websites, SaaS applications, and the public internet.      |

#### IoT

| Service          | Descriptions                                                                            |
| ---------------- | --------------------------------------------------------------------------------------- |
| **AWS IoT Core** | managed cloud service used to securely connect physical devices with cloud applications |

### Pillars of Well-Architected Framework
1. Operational Excellence
2. Security
3. Reliability
4. Performance Efficiency
5. Cost Optimisation
6. Sustainability

**AWS Well-Architected Tool:** free service that helps assess and improve cloud workloads based on the six key pillars


# Summary
This is a long module because it covers more of the ad-hoc stuff related to the cloud and I did not really want to split it up. However, these are more on the administrative and compliance guidance and not really the core functionality of the cloud.

And with that, we are done with the AWS Cloud Practitioner Essentials! It has been an eye-opening journey but I do feel that I was given more of a sneak peek and I look forward to potential applications of the knowledge I have learned.

![alt](/assets/images/weird_pikachu.jpeg)
Finally dones! Onto the next learning journey~
