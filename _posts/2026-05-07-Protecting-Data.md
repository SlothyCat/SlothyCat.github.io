---
title: "3.3 Protecting Data"
date: 2026-05-07 22:56:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/data.jpg
  alt: Protecting Data
---

# Introduction
Is it time to look at slightly simpler stuff? I think Data should be kind of simple, right...


## Data Types and Classifications
Organisations have to classify data as different data has different sensitivity. Here are some data types that are  pretty self-explanatory:

| Data Type                 | Description                                                             | Examples                                             |
| ------------------------- | ----------------------------------------------------------------------- | ---------------------------------------------------- |
| **Regulated data**        | Governed by third-party standards or law                                | Credit card data (PCI DSS), healthcare records       |
| **Trade secrets**         | Internal processes/knowledge unique to the org                          | Proprietary formulas, internal workflows             |
| **Intellectual property** | Creations protected by law                                              | Copyrights, trademarks, patents                      |
| **Legal information**     | Court records — mix of public and private                               | Public filings + redacted PII                        |
| **Financial data**        | Internal company finances or personal payment info                      | Bank accounts, transaction records                   |
| **Proprietary data**      | Data owned exclusively by the org                                       | Unique internal datasets, trade secrets              |
| **PII**                   | Personally Identifiable Information — ties data back to an individual   | Name, DOB, address, mother’s maiden name, biometrics |
| **PHI**                   | Protected Health Information — health details specific to an individual | Medical records, health status, healthcare payments  |

PHI is a subset of sensitive data specific to healthcare. Governed by HIPAA in US. 

Data can also be classified as Human Readable and Non-Human Readable. A combination would be like a barcode with printed numbers below it.

#### Data Classification Levels
Classification matters as it determines the access controls, handling procedures and permissions.

|Classification|Description|Access|
|---|---|---|
|**Public / Unclassified**|Anyone can view|No restrictions|
|**Sensitive**|Includes IP, PII, PHI — needs protection|Restricted to authorised users|
|**Confidential**|More sensitive than general data|Elevated access rights required|
|**Private / Classified / Restricted**|Sensitive internal or government data|May require NDA or specific clearance|
|**Critical**|Must always be available|High availability and uptime processes required|

> Critical classification is about availability, not just confidentiality!
{: .prompt-info}

#### Regulated Data & Governing Standards

|Data Type|Governing Standard/Law|
|---|---|
|Credit card data|PCI DSS (Payment Card Industry Data Security Standard)|
|Health information (US)|HIPAA|
|Personal data (EU)|GDPR|
|Government classified data|National security classification frameworks|

## States of Data
Data exists in 3 states: At rest, In transit and In Use.

|State|Definition|Where It Lives|
|---|---|---|
|**Data at rest**|Stored on a storage device, not actively moving|HDD, SSD, flash drive, database|
|**Data in transit**|Moving across a network|Network links, switches, routers, firewalls|
|**Data in use**|Being actively processed|RAM, CPU|

#### Data at Rest
It is **data stored on any storage medium**, whether encrypted or not. We can protect them by, of course, encryption and access control.

#### Data in Transit
This is **data moving across a network**. We should obviously encrypt these again with protocols like TLS, IPsec or Site-to-Site VPN and make use of a firewall and IPS to allow only good traffic.

#### Data In Use
This is the **data loaded into RAM or being processed by the CPU**. It is almost always decrypted since the CPU needs to read it to operate on it.

This is dangerous because attackers can just look at the data in use, which is unprotected.


#### Data Sovereignty
On the side note, data stored within a country is **subject to that country's law** and we need to remain compliant to them, such as the GDPR.

#### Geolocation
We can make use of **location data** to determine if we should grant the user access based on his/her current location.

> Technologies used: GPS, 802.11 Wi-Fi positioning, mobile carrier data
{: .prompt-info}

## Protecting Data
Data protection goes beyond encryption. We need different techniques for different threat models! We will cover familiar stuff again here!

The implementations that we already know:
1. Encryption
2. Geofencing (Geolocation restriction)
3. Hashing (pre-image resistance and collision resistance)
4. Obfuscation
5. Data Masking
6. Tokenisation (remember bank example)
7. Segmentation (reduce breach impact)
8. Permission Restrictions (access control)


# Summary
As I thought, this is a rather short chapter on data. Even though it is short, it is exactly what we are trying to protect in the end. All those firewalls and network security measures that we have gone through are all to protect our precious data!

![Alt text](/assets/images/anime_wall.jpeg)
A wall with Anime drawings in Taiwan.