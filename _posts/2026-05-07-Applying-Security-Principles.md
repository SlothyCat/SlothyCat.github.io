---
title: "3.2 Applying Security Principles"
date: 2026-05-07 19:00:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/applying.jpg
  alt: Applying Security Principles
---

# Introduction
Sounds like it might be stuff that we have previously covered? What are these security principles, hmm...

## Secure Infrastructure
We can work on the security of the network by making use of security zones and reducing the attack surface to have a secure infrastructure.

#### Security Zones
It is a logical grouping of network devices by use or access type. The zones make firewall rules easier to write, read and maintain. Normally, we will have policies like Untrusted cannot go into Trusted and other policies.

Common zone names include: Trusted/Untrusted/Inside, Screened/DMZ, servers and databases

#### Network Security Device
The first thing that comes to mind will definitely be our **firewall**, but there are also other device types involved like **honeypot, jump server, network sensors and load balancers**.

A jump server allows a controlled access point for sensitive zones, while load balancers distribute the traffic to make the network more resilient and available.

#### Reducing Attack Surface
On the infrastructure side, we can reduce it by:
1. auditing and reviewing code before deployment
2. Block unnecessary ports on firewalls
3. monitor traffic in real time to detect suspicious patterns
4. least privilege 
5. encrypt all data

#### Physical and Logical Cable Security
We have been securing all the virtual side, and of course, we cannot forget about the physical side as well. We can choose to make use of these as controls:

|Protection Type|Examples|
|---|---|
|Physical|Locked cable runs, secured network drops in offices and conference rooms|
|Logical|802.1X port authentication — only authorised devices can connect to a port|
|Encryption|Application-layer encryption ensures captured packets are unreadable|

#### Remote & Site-to-Site Connectivity
For remote users and branch offices, we have to make use of extra encryption to protect data coming from the public internet. For example, you are **working from home**, and you want to remote access in, all ur data is now moving on the internet, and we need to make sure that this is safe even if there is someone sniffing it.


## Intrusion Prevention
We will cover things that we have seen before, but in more detail. The key stuff that we are focusing on right here is the Intrusion Prevention Systems (IPS) and Intrusion Detection System (IDS).

#### Their differences

| Property           | IDS (Intrusion Detection System) | IPS (Intrusion Prevention System) |
| ------------------ | -------------------------------- | --------------------------------- |
| Traffic visibility | Yes                              | Yes                               |
| Can alert          | Yes                              | Yes                               |
| Can block traffic  | **No**                           | **Yes**                           |
| Placement          | Passive (out of band)            | Inline (in band) or passive       |

The main difference is whether it can block traffic. If IPS is passive, it will behave like IDS since it cannot block in real time when it is not inline.

IPS Detects:
- Known OS or application exploits
- Buffer Overflows
- SQL Injection
- Generic sus or malicious traffic patterns

#### Fail-Open vs Fail-Closed
This applies to **inline devices only**. This talks about what happens to the traffic when the device crashes or loses power. **Fail-Open** is when the traffic can continue to flow, and the network stays up, but unprotected if the device happens to be an IPS. **Fail-Closed** means the network goes down.

One focuses on Availability, and one focuses on Security.

#### Active (Inline) Monitoring
The IPS can sit directly in the traffic path between 2 networking points, for example, between a firewall and a switch.

#### Passive Monitoring
The IPS can also sit out of band; a copy of the traffic is sent to it via a **port mirror or network tap**. IPS is mainly for analysis here

| Method                 | Description                                                                        |
| ---------------------- | ---------------------------------------------------------------------------------- |
| **Port mirror / SPAN** | Switch Port Analyser — switch duplicates traffic from a port and sends copy to IPS |
| **Network tap**        | Physical device inserted into a cable to passively copy traffic                    |

## Network Appliances
Here we will learn more about network appliances that I have never seen before... Okay, good luck!

#### Jump Server
This is a **hardened device** inside the network that serves as a **controlled entry point for external administrators**.

External Admin will connect to the Jump server, and then they can SSH to the internal device. This provides a **controlled, auditable path for remote admin access**. This must be hardened as a breach in this will mean access to everything an admin can access too!

#### Proxy Server
This is the middleman sitting between the device and other devices (or the internet). It can be either Explicit or Transparent. 

The **Forward Proxy** controls outbound traffic while the **Reverse Proxy** protects internal web servers and filters inbound traffic.

Proxy can also help with **caching**, **URL filtering**, **content scanning** and also **NAT**! Finally, something I know!

#### Load Balancers
Similar to IPS, this also has the Active/Active and Active/Passive configurations. It distributes incoming traffic across multiple servers to maintain efficiency and for fault tolerance. 

It can maintain **one consistent TCP** for internal users and **SSL offload** (it just handles encryption and decryption more efficiently, but that means cleartext traffic between server and load balancer), **caching**, **prioritisation** and **content switching**.

#### Sensors, Collectors & SIEM
Our data sources for all the different logs are sensors that generate security-relevant data.

We have a collector, which is the centralised database that aggregates all that sensor data. This can be either:
- **Proprietary Console**: Specific to one vendor
- Security Information and Event Manager (**SIEM**): Vendor agnostic, collects from diverse device types

SIEM has the ability to consolidate, correlate, compare and report.

## Port Security
We have learned previously that we should make use of 802.1X for our ports, and we will learn more about EAP now, too. The 3 components that work together for Port Security are:
1. Client (Supplicant)
2. Authenticator (Switch/Access Point)
3. Authentication Server

#### Extensible Authentication Protocol (EAP)
It is a **flexible auth framework, not actually a single protocol**... It can be implemented across wired switches, wireless APs and VPNs by different vendors. It defines how auth messages are structured and exchanged. It happens in the transport layer with many of its variants.

#### 802.1X - Port-Based Network Access Control
It is the **IEEE standard that uses EAP** to enforce auth at the port level before granting network access. It works with RADIUS, LDAP, TACACS+, Kerberos and Active Directory, which I assume is the Auth servers.

#### The 3 Components and the workflow

| /Role                     | Device                                             | Function                                                    |
| ------------------------- | -------------------------------------------------- | ----------------------------------------------------------- |
| **Supplicant**            | End user / client device                           | Initiates connection, provides credentials                  |
| **Authenticator**         | Switch or wireless AP                              | Gatekeeps network access; passes credentials to auth server |
| **Authentication Server** | RADIUS, TACACS+, LDAP, Kerberos / Active Directory | Validates credentials and signals allow or deny             |

**Workflow**:
1. **Supplicant connects** — no network access granted yet
2. **Authenticator sends EAP Request** — asks for identity
3. **Supplicant sends EAP Response** — provides device/user identity
4. **Authenticator forwards to Authentication Server** — passes identity along
5. **Auth Server requests credentials** — asks for username, password, certificate, etc.
6. **Authenticator relays request to the Supplicant**
7. **Supplicant provides credentials** — sent back through authenticator to auth server
8. **Auth Server validates** — if credentials match, sends a success signal
9. **Authenticator opens port** — supplicant is granted network access

It is a:
C: Hi
A: Hi, who are you
C: I am C!
A: Hey, S, do you know C?
S: Yeah, but I need his ID to check if he is really C
A: You heard the man, gimme your IC
C: Okay, here you go
A: Here you go
S: seems legit
A: okay u can come in


## Firewall Types
We will learn more about the various Firewalls present! Firewalls are used to control traffic flow between 2 network points.

#### UTM - Unified Threat Management
This is an **all-in-one appliance** bundling many security functions into a single device.

Other names: Web Security Gateway, all-in-one security appliance

It has several features:
URL filtering, Malware identification, Spam filtering, WAN connectivity, IDS/IPS, Bandwidth shaping and VPN concentrator.

However, it only works on the **transport layer**, and its performance degrades with more features enabled.

#### Next-Generation Firewall (NGFW)
This operates in the application layer, with **full application awareness**.

Other names: Application Layer Gateway, Stateful multilayer inspection, deep packet inspection.

It performs a full packet decode of all traffic and then finds its application layer content and makes decisions. It has more control right now since it does not rely on port numbers alone, but it is **based on application identity**.

#### Web Application Firewall
This is mainly used to **inspect input into web applications**, for HTTP and HTTPS traffic. This primarily focuses on SQLi, XSS and other web-based attacks. This is often deployed with NGFW and is required by the PCI DSS (Payment Card Industry Data Security Standards)


## Secure Communication
We will learn about VPN, SSL/TLS VPNs, IPsec, SD-WAN and SASE here. So many things here :o

#### VPN Fundamentals
VPN (Virtual Private Network) encrypts traffic and tunnels it across a public network (the internet) to a VPN concentrator, an endpoint that decrypts traffic and passes it into the internal network.

#### IPsec Tunnelling
Since the original IP header and data cannot be sent as it is through the internet, we have to wrap them around

```
IP header | IPsec header | Enc(original IP header + data) | IPsec trailer
```

The IP header is the VPN, and it will strip the outer layers and pass the original IP header and data into the internal network.


#### SSL/TLS VPN vs IPsec VPN

|Property|SSL/TLS VPN|IPsec VPN|
|---|---|---|
|Protocol|SSL/TLS|IPsec|
|Port|TCP 443|UDP 500 / 4500|
|Firewall traversal|Easy — uses standard HTTPS port|May be blocked by some firewalls|
|Use case|**Remote access** — individual user to corporate network|**Site-to-site** — two fixed locations|
|Client required|VPN client or browser-based|Configured on edge firewalls/routers|
|Credentials|Username/password, certs, or shared key|Certificates or pre-shared keys|
|Also called|Remote access VPN|Site-to-site VPN|
|Always-on option|Yes — auto-connects on device startup|Yes — transparent to end users|

**Site-to-Site VPN**: Firewalls at each location acting as VPN endpoints. No client software is needed on individual devices. Traffic is encrypted automatically between sites.

#### SD-WAN - Software Defined WAN
In a traditional WAN, all traffic goes through the central data centre before going to cloud services. SD-WAN is more flexible as **WAN connections can route directly to cloud services** without going through the central data centre

#### SASE - Secure Access Service Edge
**SD-WAN + cloud security.** Security controls live in the cloud. Users can connect to the cloud via SASE.

|VPN (Traditional)|SASE|
|---|---|
|Single concentrator endpoint|Distributed cloud-based security edge|
|Security at the perimeter|Security follows the user to the cloud|
|Designed for on-prem data centers|Designed for cloud-distributed apps|

# Summary
This chapter is a lot more content-heavy, with more focus and emphasis on the network. Would possibly take more time and practice to be more familiar with the topic.

![Alt text](/assets/images/yellow_trees.jpeg)