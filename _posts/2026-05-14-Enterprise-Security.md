---
title: "4.5 Enterprise Security"
date: 2026-05-14 22:10:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/enterprise_security.jpg
  alt: Enterprise Security
---

# Introduction to Enterprise Security
We will learn more about how safety in an enterprise is maintained, at least in theory, here. Since I am doing an internship now as I am writing this, it feels rather special as I will cross-check with the actual practices of my company. I think my company would be quite secure since it is a financial firm.


## Firewalls
Firewalls control traffic using ACLs that are evaluated from top to bottom, with implicit deny at the bottom.

#### Network-Based Firewalls
There are traditional and NGFW. It can encrypt traffic, acting as the VPN endpoints. It can sit in the ingress and egress of the network, and also act as the NAT and dynamic routing

#### Next Generation Firewall
aka app layer gateway, stateful multilayer inspection and deep packet inspection. Every packet is analysed, categorised, and a security decision is determined. 


Traditional will make forwarding decisions based on protocol and port number. While NGFW will guess the app based on the protocol and port number.

#### Firewall Rule Base (ACL)

|Rule placement|Best Practice|
|---|---|
|Specific rules|Place at the **top** — matched quickly|
|Generic/broad rules|Place **lower** in the list|
|Implicit deny|**Bottom of every rule base** — anything not explicitly allowed is denied|


#### Screened Subnet (DMZ)
A firewall sits between the Internet and the screened subnet and the internal network. direct traffic to the screened subnet instead of the internal network.

#### IPS - Intrusion Prevention System
It monitors traffic in real time and blocks malicious traffic. It is normally integrated as a module inside NGFW with its own rule base.

| |NGFW Policy/ACL|IPS|
|---|---|---|
|L7 focus|**What the traffic is** (app identity, user, category)|**Whether the traffic is malicious** (exploits, anomalies, signatures)|
|Action basis|Classification + business policy|Threat intelligence + CVE signatures|
|Example|"Block TikTok"|"Block CVE-2024-XXXX exploit in HTTP"|

I think this might be the difference between the NGFW and IPS that I asked Claude about.

There are 2 detection methods used by IPS: **signature-based or anomaly-based**. Signature matches known attack patterns, while anomaly looks for generic attack patterns without a specific signature.

Rules in an IPS can be **grouped into categories** with a single allow/block disposition per group. This helps to manage thousands of signatures efficiently.

However, **false positives are common for large rule base**s, so we need to have a balance between security and accuracy.

## Web filtering
We want to limit what users can access online beyond just the firewall, allowing and denying. We will go through some methods to filter for content.

#### URL / Category Filtering
We can **filter by a specific Fully Qualified Domain Name or category.** We can either choose to adopt an allow list or a deny list for the filter. This is integrated into the NGFW. 

This does not cover mobile users off-network.

#### Proxy-Based Filtering
It can do URL filtering, caching, access control and malware scanning.

There is a difference between an explicit and a transparent proxy. 

|Type|Configuration|User Awareness|
|---|---|---|
|**Explicit**|Proxy IP/port manually configured in app/OS|User knows proxy is in use|
|**Transparent**|No client config required; proxy intercepts automatically|User unaware|

**Forward Proxy**: both the user and the proxy are inside the network.

#### Agent-Based Filtering
Software is **installed directly on user devices**, and that filtering decision is done on the device. This works regardless of the nature of the network, and it requires regular updates pushed to all agents (latest URL category lists)

This is best for companies with remote workforces.

#### DNS Filtering
It **blocks access for DNS resolution** for known-bad domains. The DNS server will check against its threat intelligence lists. This works on all traffic, not just browser requests, so it is stronger than URL filters.

| Scenario                          | URL Filter      | DNS Filter  |
| --------------------------------- | --------------- | ----------- |
| Browser visits malicious site     | Blocked         | Blocked     |
| a Malware calls C2 server via DNS | **Not blocked** | **Blocked** |

This is updated automatically via real-time threat intelligence, and there are both public and commercial lists available.


#### Reputation-Based Filtering
Sites are now **scored by risk level**, and this is typically **automatically scanned**. Based on the reputation level, specific actions are allowed. 

Since this is like a table, **manual overrides are possible** when automated reputation is different from the admin's judgment.



## Operating System Security
I guess we will learn how to keep the OS secure too.

#### Active Directory
This is a database of everything on the network that includes the computers, user accounts, file shares, and even printers. This is normally Windows-based.

We can manage the authentication from here by letting users log in using their credentials for AD. This makes centralised access control easier as we can determine which user can access which resources.

#### Group Policy
The **Group Policy Management Editor** can configure the settings on AD computers and users.

| What Group Policy Can Configure | Examples                                                  |
| ------------------------------- | --------------------------------------------------------- |
| Login scripts                   | Run scripts when a user connects to the network           |
| Network configuration           | Quality of Service settings                               |
| Security parameters             | Password policies, account lockout, software restrictions |
| Per-user settings               | Different policies for different users or OUs             |
| and Per-device settings         | Different policies for different machine types            |


#### Security-Enhanced Linux
Linux uses Discretionary Access Control by default. Users will control permissions on their own resources. SELinux implements Mandatory Access Control, where all the rights and permissions are assigned by a central administrator.

It adopts least privilege and possesses breach containment.

| Property                    | DAC (Default Linux)       | MAC (SELinux)              |
| --------------------------- | ------------------------- | -------------------------- |
| Who sets permissions        | The resource owner / user | Central administrator      |
| User discretion             | Yes                       | No                         |
| Least privilege enforcement | Weak                      | Strong                     |
| Suitable for                | General use               | High-security environments |


## Secure Protocols
There are many protocols in use and we should adopt secure versions.

|Function|Insecure Protocol|Port|Secure Replacement|Port|
|---|---|---|---|---|
|Remote console|Telnet|23|**SSH**|22|
|Web browsing|HTTP|80|**HTTPS**|443|
|Email (receive)|IMAP|143|**IMAPS**|993|
|Email (receive)|POP3|110|**POP3S**|995|
|File transfer|FTP|21|**SFTP**|22|

Port number alone does not guarantee the encryption; we should verify with the server configuration and confirm it via packet capture.

#### Network-Level Encryption
If we cannot change to a secure protocol, encrypt at the network level using:
- WPA3
	- Wireless access point encrypts all data sent over, even if apps do not support encryption
- VPN
	- Creates an encrypted tunnel between the device and the VPN concentrator

VPN may require additional software installation.

## Email Security
Email spoofs are common because the SMTP does not have built-in authentication. 3 DNS-based mechanisms work together to validate the email. SPF (authorised sending servers), DKIM (digital signature on transport) and DMARC (policy for what to do if validation fails and reporting.)

#### Email Spoofing
Since SMTP does not have native authentication, anyone can put any name in the From field. You might receive an email claiming to be from Alice, but there is no way to verify that without extra checks.

**Mail Gateway**: This is the organisation's gatekeeper that checks for inbound email before delivering to inboxes. This can either be on-premises or cloud-based. It checks emails to see if they came from a valid source. Valid sources will go to the inbox while invalid ones go to the spam or the discarded.

#### SPF - Sender Policy Framework
Defines which mail servers are authorised to send email on behalf of a domain. It is added as a DNS TXT record that is publicly queryable. The receiving mail server will check the sender's DNS for the SPF record. 

#### DKIM - DomainKeys Identified Mail
Adds a digital signature to the email transport so the receiving server can verify the email has not been tampered with during transit. 

The mail server signs email with private key. Public key is stored as a DNS TXT record. Receiving server will retrieve the public key, and validate the signature.

>Not Visible in the email body. Must check headers to see it. This is just configured on the mail server.
{: .prompt-info}

#### DMARC - Domain-based Message Authentication, Reporting & Conformance
This is the final step. It specifies what to do with the emails that have failed validation and enables compliance reporting.

Here are the three policies that can be implemented:

| DMARC Policy | Action on Failure                           |
| ------------ | ------------------------------------------- |
| none         | Accept all messages (monitor only)          |
| quarantine   | Send failed emails to spam folder           |
| reject       | Reject emails that fail validation entirely |

This can also be added as a DNS TXT record. We can specify a reporting destination so that the receivers will send a report of the pass fail statistics to that destination. The domain owner can see how many legitimate and spoofed emails are being sent in their name.

> DNS TXT record simply refers to the text returned in the DNS record.
{: .prompt-info}



## Monitoring Data
There are different ways for us to protect data in its 3 states.

#### File Integrity Monitoring (FIM)
This monitors if there are any changes to application executables and libraries because these are not supposed to change usually. Different tools can be used to achieve this.

|Tool|Platform|How It Works|
|---|---|---|
|**SFC** (System File Checker)|Windows|On-demand scan; replaces modified OS files with known-good copies|
|**Tripwire**|Linux|Monitors for file changes; supports real-time alerting|
|**Host-based IPS**|Both|Monitors all files on the OS file system; blocks attacks + performs FIM|

#### Data Loss Prevention (DLP)
We monitor and block any sensitive data from being transferred without authorisation.

It is split into the 3 data states as well:

|Data State|DLP Type|Where It Runs|
|---|---|---|
|**Data in use**|Endpoint DLP|On the local device — monitors active memory|
|**Data in motion**|Network DLP|Network appliance or NGFW module — monitors packets in real time|
|**Data at rest**|Storage DLP|Software on the server/OS — monitors files on disk|

It can be deployed on network appliances, endpoint agents, cloud and also email.

Actually, even USB.

## Endpoint Security
Okay now we have some of the layered defences for our endpoints. We can make use of edge firewall to protect the perimeter and access control to limit what the device can access.

As we recall, there is a posture assessment for devices to make sure they are compliant before granting them network access.

This can be done with NAC agents:

|Type|How It Works|Always Running?|
|---|---|---|
|**Persistent agent**|Pre-installed; monitors continuously|Yes|
|**Dissolvable agent**|Runs at login; removes itself after check|No|
|**Agentless NAC**|Integrated with Active Directory; runs at login/logoff only|No (AD-dependent)|

We also make use of Antivirus / Anti-Malware and EDR.

#### XDR - Extended Detection and Response
This scales EDR across multiple systems and data sources simultaneously. Basically, with a larger scope to defend against attacks that involve more than just the endpoint.

|Enhancement over EDR|Detail|
|---|---|
|Multi-system correlation|Sees attack patterns spanning multiple endpoints|
|Network traffic data|Adds traffic flow analysis to endpoint telemetry|
|User behaviour analytics (UBA)|Builds baseline of normal user activity; flags anomalies|
|Fewer false positives|Broader context = more accurate classification|
|Faster investigation|Automation across all data sources speeds up response|


# Summary
This chapter took quite a bit of time, unexpectedly, as I was sick-ish and restless. But I think this is a good chapter as it helps me to correlate different stuff I see in my work with what I am learning over here.

![alt text](/assets/images/strawberry_cake.jpeg)
Nom nom 🍰