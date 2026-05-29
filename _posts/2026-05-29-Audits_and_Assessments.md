---
title: "5.5 Audits and Assessments"
date: 2026-05-29 18:25:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/audit_and_assessment.jpg
  alt: Audits and Assessments
---

# Introduction to Audits and Assessments
Audits are conducted to ensure compliance. They can be internal or external. Attestation is a formal opinion on the truth of the audit results.

## About Audits in the company
#### Why Audits
Audit helps us to:
- **Examine** IT infrastructure, software, and network devices
- **Verify policies and procedures** are protecting against modern threats
- Find vulnerabilities before attackers do
- Confirm **compliance** requirements are being met

#### Attestation
As mentioned, this is **an opinion of truth associated with the result of an audit**. The attesting party formally states that the audit results are accurate, and this is often an executive or third-party auditor.

#### Internal Audits
This is performed within the organisation **by its own staff.** Normally, before external audits, so as to pass the external checks too. An **audit committee** will be formed, and they will collect **self-assessments** from the organisation to get a consolidated view of compliance status.

#### External Audits
This is performed by a third party. This is required when **regulation** mandates it. For example, the MAS audit team is at my internship company doing audits now oop.

## Penetration Tests
There is actually more than just red teaming in the digital world; it can be **physical** as well. We will also explore more about the differences between the red and blue teams and understand what reconnaissance is. 

#### Physical Penetration Testing
**Physical access to a device can bypass all digital security controls**. This is because the attacker can, for example:
1. Modify the boot process
2. Boot from external media
3. Modify or Replace OS files

Funny enough, not too sure if this is possible, but physical pen testers can try to enter the building without a key, test doors, windows and elevators and discover what kind of access that they will get once they get in physically.

#### Red Team VS Blue Team
`Red` - **Offensive**, find vulnerabilities and exploit
`Blue` - **Defensive**, identifies attacks in real time and blocks them, patches and improves detection

They work hand in hand.

#### Environment Knowledge Levels

|Type|Information Provided|Also Called|
|---|---|---|
|**Known environment**|Full disclosure of all systems to be tested|White box|
|**Partially known environment**|Some information provided — ensures certain systems are tested|Grey box|
|**Unknown environment**|No information provided — tester finds everything independently|Blind test / Black box|

## Reconnaissance
This is information gathering before an attack begins. This builds a complete picture of the target environment.

The goal here is to understand the security tools, installed servers, running applications, network map, IP configuration and remote site connectivity.

#### Passive Reconnaissance / OSINT
We can gather information from sources that do not directly connect to the target network.

| Source                 | Example                                         |
| ---------------------- | ----------------------------------------------- |
| Social media           | Employee posts revealing infrastructure details |
| Corporate website      | Public information about the organisation       |
| Online forums / Reddit | Posts discussing internal systems               |
| Social engineering     | Calling employees to extract information        |
| Dumpster diving        | Documents discarded in trash                    |
| Third-party companies  | Vendors who do business with the target         |

#### Active Reconnaissance
Directs queries to devices on the target network, **leaving evidence in the log files.**

|Technique|Example|
|---|---|
|Ping scan|Check which hosts are alive|
|Port scan|Identify open ports and services|
|DNS query|Query corporate DNS server|
|OS fingerprinting|Identify operating systems on devices|
|Service/version scan|Identify software versions running on ports|

> This can be detected by the blue team
{: .prompt-warning}


# Summary
This chapter covers mainly **audits** and **penetration testing**. I have never done an audit before, but I do see the company staff getting more stressed when the audit comes. I also get handed urgent work so that we can show the external audit team certain evidence. Red teaming would be fun to engage in, I guess? I will do the TryHackMe soon after this, heheh, I'm quite curious.

P.S I actually finished this a lot earlier but I was caught up in other stuff and forgot to upload

![Alt text](/assets/images/tsukiji_fish_market.jpeg)
So many seafoodo 🐟