---
title: "5.6 Security Awareness"
date: 2026-05-29 18:25:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/security_awareness.jpg
  alt: Security Awareness
---

# Introduction to Security Awareness
In this chapter, we will learn more about creating awareness for security, focusing on the why and how of security, especially for employees who are not technically trained.

## Creating Security Awareness
#### Phishing Campaigns
This is a controlled phishing simulation sent to the user community to measure how many people will click on the malicious link. 

How can the average person look out for phishing emails?
- Spelling / Grammar errors
- Suspicious domain name
- Unusual Construction
- Unexpected Attachments
- Requests for personal information

![alt text](/assets/images/cat_pointing.jpg)

#### Anomalous Behaviour Recognition
Identify activities that deviate from normal. This is being categorised into 3 types:

|Category|Description|Examples|
|---|---|---|
|**Risky behaviour**|Actions that create security risk|Modifying a host file, replacing OS files, uploading sensitive files|
|**Unexpected behaviour**|Activity outside normal patterns|Login from another country, unusual spike in data transfers|
|**Unintentional behaviour**|Human error|Typing the wrong domain name, misplacing a USB drive, misconfiguring security settings|

#### Security Awareness Team
This is a team focused on **user security behaviour**. Some of their responsibilities include:

| Responsibility           | Detail                                                                       |
| ------------------------ | ---------------------------------------------------------------------------- |
| Monitoring and reporting | Automated alerts and daily reports on security events                        |
| Training                 | Creates and delivers online and in-person security training                  |
| Customised content       | Training tailored by job function or compliance requirement                  |
| Metrics tracking         | Tracks phishing click rates, password manager adoption, MFA use, and more    |
| Stakeholder reporting    | Reports metrics to managers and stakeholders showing security posture trends |
| Materials                | Classroom training, posters, emails, intranet content                        |

After a security event.
- **First** occurrence: User training addressing the specific issue
- **Recurring**: Extended training and review of security configurations for that user

## User Training
This should be a **role-specific** and **ongoing** process. Users are both a security asset and a potential insider threat; we can make the users active defenders for security.

#### Training Principles
- Provide training **before users are connected** to the network for the first time
- Training should be **role-specific**
- **Track** who has not been trained and who has been
- **Document** all security policies and make them accessible

Third parties also need training when connecting to the network.

#### Situational Awareness
**Users should always be looking for threats in their day-to-day work.** This includes email phishing, physical attacks and social engineering.

> Social Engineering would be like requests for information that seem unusual or urgent
{: .prompt-info}

#### Insider Threats
Insider threats are hard to identify, and we need to have defence-in-depth.

|Control|Detail|
|---|---|
|Multiple approvals|Any critical system change requires sign-off from more than one person|
|Active file monitoring|Immediate alert if any critical file changes|
|Difficult bypass|Processes designed to make circumventing controls hard|
#### Password Management Training
Password requirements and enforce them administratively wherever possible. We can try to educate and teach about password managers.

#### Removable Media and Cables
Users should not use unknown media or cables, as they can either install malware or take data out.

#### Social Engineering Awareness
**Users can be trained to recognise common social engineering techniques** and understand how attackers exploit human trust, urgency and authority. We should report any suspected social engineering to the IT security team immediately.

**Operational Security**: It trains users to think from the attacker's perspective and understand why data is sensitive and needs to be protected

#### Data Handling
Users who work with a lot of data need to **understand which data is sensitive** and how we can apply additional security to handle it. There are also legal and policy obligations around data sharing.

#### Remote Work Security
Something that I have been working with recently, because there is remote work for me hehehe

|Concern|Control|
|---|---|
|Family/friend access|Users must not allow others to use work devices|
|Endpoint security|Additional security on devices outside the building|
|VPN access|Increased security requirements for all VPN connections from home|

# Summary
This chapter covers more of the **human aspect** of security. We can implement all the controls we want in the digital world, but if humans get lazy and try to prioritise convenience, then the controls will not be as effective. **Balance** between convenience for business and security, I guess. And we are finally done with all the chapters for Security+! Time to lock in to prepare for the exam!

![alt text](/assets/images/jinglebells.jpeg)