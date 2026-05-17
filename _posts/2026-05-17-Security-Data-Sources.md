---
title: "4.9 Security Data Sources"
date: 2026-05-17 16:45:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/security_data_sources.jpg
  alt: Security Data Sources
---

# Introduction
We will learn more about data logs over here. I have learned from previous chapters that we always seem to put different data sources into a SIEM and then we can see all the information there. I wonder if all data logs are visible there.

## Firewall Logs
Firewalls **monitor all traffic between inside and outside of the network** and each log entry will typically contain:
1. Time and date
2. Source IP
3. Destination IP
4. Port Numbers
5. Disposition (Allowed or Blocked)
For **NGFW**, there is also information on the application in use, URL or URL category and suspicious data or anomalies in traffic flow.

## Application Logs
SIEM seems to lie here, for all the application logs rolled up here and filterable. There are also **different logs for different operating systems** as well. Event Viewer for Windows and `/var/log` directory for Linux and macOS

## Endpoint Logs
Every endpoint will also generate extensive log data. This includes
1. Login and logoff events
2. System events and running processes
3. Device management events
4. Directory services activity
All endpoint logs can also be rolled up to a SIEM for correlation with network and device logs.

## OS Security Logs
OS system **maintains security-specific log files** too. It can be 
1. Individual application monitoring
2. Brute force attack detection
3. Changes to critical system files
4. Authentication events

> **Not all information goes to the SIEM**; only information important enough to make security decisions is sent
{: .prompt-tip}

## IPS / IDS logs
IPS and IDS **usually sit with the NGFW**. Some fields they will include would be
1. Timestamp
2. Alert class
3. Priority Level
4. Source IP and port
5. Destination IP and port
**All IPS events can be rolled into SIEM for cross-device correlation**.

## Network Infrastructure Logs
These include switches, routers, WAPs, and VPN concentrators. Information will include
1. Routing table changes
2. Authentication errors
3. Network attacks

## Metadata
These are hidden data in documents, emails, browsers and images.

|Source|Metadata Examples|
|---|---|
|Email headers|Sending servers, destination addresses, SPF info, signatures|
|Mobile device photos|Device make/model, GPS coordinates of where photo was taken|
|Browser|OS type, browser type, IP address|
|Word/spreadsheet documents|Creator name, address, phone number, title|
## Vulnerability Scan Logs
Vulnerability scans will also generate logs that identify:
1. Devices without firewalls or antivirus
2. Misconfigured systems
3. Unsupported OS
4. Network File System (NFS) shares readable by anyone
5. Known CVEs on installed applications

## SIEM - Reports and Dashboards

#### Automated Reported
These are built into SIEM or 3rd party report generators and must actually be read to be useful. Be specific about what you need to have a report in an acceptable amount of time

#### Dashboards
At-a-glance summary of current security status.

This is customisable or has predefined views. Designed for real-time viewing and is common in SOC. Typically shows: active firewall rules, recent warnings, users and devices on the network

## Packet Captures
This is the deepest level of network analysis as it captures every bit and byte traversing the network

|Tool|Detail|
|---|---|
|**Wireshark**|Popular third-party packet capture utility; works on wired and wireless|
|Network devices|Some switches, routers, and firewalls can capture packets internally|

**Wireshark views:**
- **Summary pane (top):** Packet-by-packet breakdown — source, destination, protocol, info
- **Detail pane (bottom):** Full breakdown of the selected frame — Ethernet, IPv4, TCP, and application layer data
**Example:** An HTTP GET request is visible in the capture — you can read the actual command inside the packet if the traffic is unencrypted.

# Summary
I guess to a certain extent, most information goes to the SIEM, and it will be visually represented for clarity and monitoring. This feels very blue team-ish.

![alt text](/assets/images/ball_on_roof.jpeg)
A ball in Cheng Du.