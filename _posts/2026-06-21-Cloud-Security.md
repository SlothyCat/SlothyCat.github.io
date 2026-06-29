---
title: "Cloud Security"
date: 2026-06-21 20:30:00 +0800
categories: [AWS Cloud]
tags: [AWS Cloud]
image:
    path: assets/images/cloud_security.jpg
    alt: Cloud Security
---

# Introduction
This chapter seems a lot shorter than what we have gone through, and let us see if the security concepts covered are easier for me to understand now that I have the Security+ muehehhe...

### Security in AWS
**Authentication and Authorisation** are covered once again, identity verification and what rights you have. Security is also a shared responsibility between the cloud and the client.

![alt](/assets/images/AWS_shared_responsibility_security.png)


### Preventing Unauthorised Access
#### AWS Identity and Access Management
IAM, **by default, means all actions are denied**. We will follow the **principle of least privilege** when providing access.

- **Policies**: JSON document that describes what API calls a user can or cannot make
- **Users**: single individual users
- **Roles**: Temporary access
- **Groups**: groupings of users. You can attach a policy to a group, and all of the users in that group will inherit those permissions.


#### AWS IAM Identity Centre
This provides a centralised management of IAM, and this can connect to an existing identity source and provide SSO service. Federated identity management!


| reService                   | Descriptions                                                                                                                                              |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **AWS IAM Identity Center** | This provides a centralised management of IAM and this can connect to an existing identity source and provide SSO service. Federated identity management! |
| **AWS Secrets Manager**     | provides a secure way to manage, rotate, and retrieve database credentials, API keys, and other secrets throughout their lifecycle                        |
| **AWS Systems Manager**     | provides a centralised view of nodes across your organisation’s accounts and Regions, and multi-cloud and hybrid environments                             |

### Network and Application Security
In the learning materials, they mentioned DDoS attacks. 

**Security Groups**: Only allow proper request traffic
**Elastic Load Balancer**: Handles traffic first before handing it off so that the frontend server will not get overwhelmed.
**AWS Regions**: Enormous capacity makes it hard to overwhelm


| Service        | Descriptions                                                                                                     |
| -------------- | ---------------------------------------------------------------------------------------------------------------- |
| **AWS Shield** | It uses a variety of analysis techniques to detect and mitigate incoming malicious network traffic in real time. |
| **AWS WAF**    | monitors network requests that come into your web applications.                                                  |

>_AWS Shield Advanced_ is a paid service that provides detailed attack diagnostics and the ability to detect and mitigate sophisticated DDoS attacks.
{: .prompt-info}


### Protecting Data
Using data encryption. Over here, they only cover Data encryption at rest and in transit but not in use.

How does Amazon encrypt?
- `S3` has encryption configured at rest.
- `EBS` has encrypted volumes and snapshots
- `DynamoDB`, server-side encryption and keys stored in `AWS Key Management System (KMS)`

| Service                                  | Descriptions                                                                                     |
| ---------------------------------------- | ------------------------------------------------------------------------------------------------ |
| **AWS Key Management Service (AWS KMS)** | create and manage cryptographic keys.                                                            |
| **Amazon Macie**                         | monitor your sensitive data at rest to make sure it's safe using ML and automation.              |
| **AWS Certificate Manager (ACM)**        | centralises the management of your SSL/TLS certificates that provide data encryption in transit. |

### Detecting and Responding to Security Incidents

| Service                    | Descriptions                                                                                                                                                                                                           |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon Inspector**       | running **automated security assessments for Amazon EC2** instances, containers, and Lambda functions. It checks applications for security vulnerabilities and deviations from security best practices.                |
| **Amazon GuardDuty** | provides **intelligent threat detection across your infrastructure and resources**. GuardDuty identifies threats by continuously monitoring streams of your account metadata and network activity in your environment. |
| **Amazon Detective**       | helps you **analyse threats** with interactive visualisations contained in a unified AWS Management Console view.                                                                                                      |
| **AWS Security Hub**       | Security Hub **brings multiple security services together** into a single place and format.                                                                                                                            |

# Summary
Hmm, mainly security solutions offered by AWS, might have other alternatives, but they position themselves to be well integrated with their products so if the client is already using a lot of AWS products, then they might as well use these too.

![alt](/assets/images/kawamura_walk_view.jpeg)
