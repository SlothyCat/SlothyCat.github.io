---
title: "2.5 Mitigation Techniques"
date: 2026-05-06 16:15:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/mitigation.jpg
  alt: Mitigation Techniques
---

# Introduction to Mitigation Techniques
Now that we have gone through the attacks and vulnerabilities. Let us quickly go through the mitigation techniques that we have.

## Network Segmentation & Access Control
We normally segment a network for the following reasons:
1. Reduce impact when there is a breach
2. isolate for performance
3. strategic security
4. compliance (PCI DSS- e.g. Payment card data needs to be on a completely isolated network segment)

There are 3 types of segmentations that we shall cover:
**Physical Segmentation**: Literally just separating the hardware. Dedicate each to its particular use.
**Logical Segmentation**: This is done via VLANs. This allows virtual separation on the same physical switch
**Virtual Segmentation**: This is software-defined zones in the cloud or VMs

#### Access Control
We can use Access Control Lists to determine which traffic is allowed or denied based on specific criteria.

We need to have: Source IP, Destination IP, Port Number, User and Time of the day.

We can also make use of **Allow and Deny Lists**. The allow list is more secure because it denies by default.

###### Windows Application Control Methods 
Windows provides multiple ways to implement allow/deny rules: Application Hash. Digital Signature, Directory path and network zone. Hash-based control is the most precise, as you know if something is modified.


## Mitigation Techniques
There are a lot of techniques, and so I will simply list them down; it is already quite familiar to see these again, actually.
1. Patching
2. Encryption
3. Monitoring & Logging (SIEM)
4. Least Privilege
5. Posture Assessment
	1. Isolate the device until it has met the security requirements before granting access
6. Decommissioning
	1. Reformat or just physically destroy

## System & End-point hardening
Hardening is making systems more resistant to attack by reducing the attack surface and strengthening security controls. I will bold those that are more interesting because a lot of concepts are actually repeated already. There are always changing default credentials and removing unused apps to reduce the attack surface.

#### Server/OS hardening
Patches, password policy, least privilege, **IP-based access control** and **Endpoint monitoring**.

#### Encryption for Hardening
File-level, disk-level, network traffic and application-level.

#### Endpoint Hardening
Endpoints are like our desktops, laptops and phones, and since all of them run different OSes, we need more platform-specific defences for them. We will also require defence in depth for this.

**Endpoint Detection and Response**: This is Anti-virus but with ML and automated response based on behaviour

#### Host-Based defences
There are host-based firewalls and host-based IPS, so that they sit closer to the endpoint

#### Open Ports & Attack Surface
ports might be opened unknowingly, so we can use Nmap to check for all open ports.


# Summary
This is a relatively short topic. I think the defences are most of the time quite easy to categorise, but the actual implementation and decision-making would be the hard part.

![Alt text](/assets/images/lhh_gym_sunset.jpeg)
Even though getting to the gym was really hard cuz of the deadly stairs but it has a really nice view!