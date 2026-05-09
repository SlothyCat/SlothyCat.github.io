---
title: "4.2 Asset Management"
date: 2026-05-09 12:07:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/asset_management.jpg
  alt: Asset Management
---

# Introduction to Asset Management
We are starting to see the business side of cybersecurity here :o.

## Procurement Process
It always starts with the end user, and then it seeks approval from IT and purchasing teams. The management will sign off, and then we can start negotiating with suppliers. We will need to decide on the payment terms, too with the supplier.

## Asset Tracking
This is more for accounting, and we need to differentiate between hardware and software.

**Hardware = capital expenditure** — depreciates over time, affects taxes.
**Software = operating expense** — does not depreciate, taxed differently.

|Property Tracked|Detail|
|---|---|
|Ownership|Who is assigned this asset|
|Device type|Laptop, desktop, mobile, router, etc.|
|Hardware vs software|Different tax treatment (see below)|
|Location|Where the device physically is|
|Components|CPU, RAM, storage, peripherals inside a device|
|Asset tag|Physical label with barcode/number attached to device|

>**Asset tags** serve a dual purpose: inventory management + security deterrent if the device is lost/stolen.
{: .prompt-info}


## Media Sanitisation
Before reusing or disposing of a device, data must be removed so it cannot be recovered.

| Method                         | Use Case                                          | Data Recoverable?              |
| ------------------------------ | ------------------------------------------------- | ------------------------------ |
| **Secure delete / overwrite**  | Reuse internally                                  | No (if done correctly)         |
| **Degaussing**                 | HDDs only — uses strong EM field                  | No — also renders HDD unusable |
| **Physical destruction**       | Shredder, pulveriser, drill, hammer, incineration | No                             |
| **Certificate of destruction** | Third-party bulk destruction                      | Confirmed destroyed            |

> Degaussing only works for magnetic drives. Will not affect SSDs and will render HDDs permanently unusable
{: .prompt-warning}


## Data Retention
If we need to keep the data, it needs to be mandated by regulation or company policy. Note that different data types will have different retention periods and storage requirements.


# Summary
This is a short chapter, but it covers more on the business side of cybersecurity, less technical but more human.

![Alt text](/assets/images/mushroom_deco.jpeg)
A cute mushroom decoration in Shibuya!

