---
title: "5.1 Security Governance"
date: 2026-05-17 17:15:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/security_governance.jpg
  alt: Security Governance
---

# Introduction to Security Governance
Are we moving onto the GRC side of things? HMMMMMM.

## Security Policies
The policies are the foundation of the company's security posture. This is literally what I read when I onboard...

#### Information Security Policies
This is a **master list of all policies required to maintain uptime, availability and security**. This can either be broad goals or detailed rules

#### Acceptable Use Policy (AUP)
This defines **what users are allowed to do with company technology**. This applies to everyone in the organisation and protects the company from legal liability.

#### Business Continuity
These are **plans for keeping operations running**. This must be planned before a disaster occurs, and it requires extensive documentation and testing.

#### Disaster Recovery Plan
This is a type of Business Continuity plan where the organisation prepares for **widespread or extended disasters**.

Disaster will include natural disasters, technology failures and human-created disasters.

> We have learned this previously in Resilience and Recovery
{: .prompt-info}

#### Security Incident Policies
Policies for incident response as discussed in the previous chapter.

**Incident Response Roles:**

|Role|Responsibility|
|---|---|
|Incident response team|Specialised, trained and tested group ready for any security event|
|IT security management|Obtains proper resources and personnel|
|Compliance officers|Ensures compliance mandates are met during the incident|
|Technical staff|Works in the trenches to solve technical problems|
|User community|Provides information about what was seen during the event|

We can take reference to the NIST SP 800-61 Rev 2.

#### SDLC - Software Development Lifecycle
This is a **structured process** for creating software from idea to deployed applications.

> Requirements -> Development -> Testing -> Deployment -> Maintenance
{: .prompt-info}

**Waterfall**: Linearly done
**Agile**: Iterative development, every iteration is a product

#### Change Management
Ensures that **every change in the system follows a formal process** to prevent downtime, confusion and mistakes. CM Documents will include:
- How often will the change occur
- Duration of change
- Process involved in making the change
- Fallback procedure if the change fails

## Security Standards
These are specific, measurable requirements that define how security must be implemented. **This is the how** while Security Policies are the what and why.

Different standards will include:
1. Password Standards
2. Access Control Standards
3. Physical Security Standards
4. Encryption Standards

## Security Procedures
This translates the policies and standards into **step-by-step actions**. For example, there is the Change Management Procedure, which was covered previously. Apart from that, there are also different procedures to take note of.

#### Onboarding Procedure
1. Provide employee handbook and AUP for sign-off
2. Create user accounts with the right access
3. Assign laptop and other required technology
4. User can now log in and access the network

#### Offboarding Procedure
Process when a user leaves the organisation, which handles what to do with the **hardware, data and account status for the account.**

> Normally, we will disable accounts and not delete them so that we can have continued access to the encrypted files and decryption keys
{: .prompt-tip}

#### Playbooks
This is a **step-by-step, documented procedure for responding to specific events**. There should be a large number of playbooks, each for a scenario. These playbooks should be reviewed and updated as new technologies are adopted or new threats emerge.

We can integrate this into automated platforms like **SOAR** - Security Orchestration, Automation and Response.

SOAR integrates many 3rd party security products into one platform and automates connections between them. This frees the security team to focus on high-value work

#### Governance Structure
It can be split into 3 ways
1. **Board and Committee**
	1. The board sets broad objectives, and committees are experts who determine what to implement
2. **Public vs Private sector**
	1. The public is the government, and meetings are usually open to the public
3. **Centralised vs Decentralised**
	1. Centralised is 1 group that handles decisions for the entire organisation, while decentralised is a group that is closest to the work will decide


## Security Considerations
We should be aware of the regulations and other considerations involved so that we follow the guidelines and law.

#### Key Regulations
**SOX - Sarbanes-Oxley**: Focuses on Financial data protection and availability
**HIPAA - Health Insurance Portability and Accountability Act**: Focus on healthcare information protection

#### Legal Requirements for IT Security
We need to **follow the obligations** for reporting illegal activities, legal hold and breach disclosures.

#### Cloud and Data Sovereignty
There are guidelines on **how cloud data can be stored.** There might be data residency laws, jurisdiction for data and multi-cloud complexity if data is spread across different countries, subject to different laws at the same time.

#### Industry-Specific Security Considerations
For **different industries, there will be security considerations specific to them** as well. For example, in healthcare, since it deals with more sensitive data, there will be a stronger security posture.

#### Organisational Scope Considerations
The **size of the organisation will impact the extent of the security considered.** The greater the scope, the more complex to manage and the more secure it has to be.

## Data Roles and Responsibilities
There are different roles in data management, and they include: Data Owner, Data Controller, Data Processor and Data Custodian/Steward.

#### Data Owner
Usually, a **senior person** in the organisation who is **broadly responsible for a specific category of data**. The person is ultimately accountable for all data associated with their role.

#### Data Controller
**Manages how the data will be used** by providing instructions to the data processor. Often an internal department with responsibility for a data drive process 

> Payroll Department is the data controller, as they ensure everyone gets paid and direct the payroll company on how to process payroll
{: .prompt-tip}

#### Data Processor
The one that actually **processes or uses the data based on the controller's instructions**. This is often a 3rd party contracted to perform a specific function. It has access to user information and other sensitive data required to perform the processing task

> Payroll company is the processor. They receive instructions from the payroll department and then access employee bank details to process payroll
{: .prompt-tip}

#### Data Custodian
The one responsible for the **security, accuracy and privacy** of specific data. They ensure that the data is **compliant** and is **labelled** with sensitivity. They also manage the **access control** for that data.

# Summary
In this chapter, I learned more about the security written in documents, which acts as a reference for the companies to make decisions. The roles for managing data are also covered here, which shows the different segregation of duties and how it is being organised.

![alt text](/assets/images/kl_twin_towers.jpeg)
Here is a picture of the KL twin towers where I visited with a very special someone!