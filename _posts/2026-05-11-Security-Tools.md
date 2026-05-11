---
title: "4.4 Security Tools"
date: 2026-05-11 20:39:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/security_tools.jpg
  alt: Security Tools
---

# Introduction to Security Monitoring
Okay, now that we have finished identifying vulnerabilities and rectifying them, we have security monitoring now, which is more ongoing to detect if there is anything suspicious going on!

## Security Monitoring
Effective security monitoring requires **watching a lot of different data in real time**. SIEM will consolidate the diverse logs, and SNMP will poll devices to see if there is anything wrong. NetFlow will analyse traffic patterns, and together they can form a dashboard, actionable reports and also detect anomalies!

#### What do we even monitor?
1. Compute Resources (Auth events, login locations, services running)
2. Applications (Availability, traffic volume and unusual data transfers)
3. Infrastructure (VPN connections)

#### SIEM
Remember what SIEM does:
- **Collect logs** from firewalls, servers, routers, switches and VPN concentrators
- **Correlate** information
- Set **threshold** for alerts
- **Forensics** to go back in time to reconstruct the attack timeline

> The average breach detection time is ~9 months, so we need long-term log retention
{: .prompt-info}

#### SNMP - Simple Network Management Protocol
Built-in monitoring protocol that collects device metrics.

|Component|Description|
|---|---|
|**MIB**|Management Information Base — database of metrics on a device|
|**OID**|Object Identifier — numeric address of a specific metric in the MIB|
|**Polling**|Management station queries device on a schedule (e.g. every 5 min) — UDP 161|
|**SNMP Trap**|Device proactively sends alert to management station when threshold is exceeded — UDP 162|

OIB is the address of a particular metric in MIB, and its value is the metric value, like uptime: 5seconds

> Polling limitation: Only captures data at query intervals — misses events between polls.
{: .prompt-warning}

This is why we use **SNMP trap** so that we can react (**real-time proactive alerting**) without waiting for the poll

#### NetFlow
This is to **monitor the traffic flows and application usage patterns across the network**. Basically, we have a probe to clone the traffic for us to analyse.

| Component              | Role                                                                              |
| ---------------------- | --------------------------------------------------------------------------------- |
| **NetFlow probe**      | Captures traffic flow data (built into switch/router software or external device) |
| **SPAN / port mirror** | Provides probe with a copy of network traffic                                     |
| **Physical tap**       | Hardware tap on cable for probe access                                            |
| **NetFlow collector**  | Receives and stores flow data; generates reports                                  |

You can tell who, what app and how much from NetFlow

#### Actionable Reports & Ad Hoc Analysis

| Report Type       | Purpose                                                                 |
| ----------------- | ----------------------------------------------------------------------- |
| Compliance report | How many devices are patched vs unpatched                               |
| OS inventory      | What OS versions are in use; which need updates                         |
| New threat check  | How many systems are vulnerable to today’s announced CVE                |
| Ad hoc / what-if  | e.g. "When this OS goes EOL in 6 months, how many systems are exposed?" |

## Security Tools
We will learn more about the other tools in security here! I guess some of them.

#### Security Content Automation Protocol (SCAP)
Manage different security tools on the market and let them **identify and act on the same criteria** based on NIST guidelines. This helps with **coordination between tools** that might have used different wordings initially.

#### CIS Benchmark
Pre-built security **best-practice configurations** for OSes, apps, cloud providers and mobile devices.

In general, benchmarks are best practices to keep things secure.

#### Agent/Agentless Compliance Scanning
We need to check if the device is in compliance, so we will do this Compliance Scanning

| Property       | Agent-Based                          | Agentless                         |
| -------------- | ------------------------------------ | --------------------------------- |
| Installation   | Pre-installed on device              | No install required               |
| Always running | Yes — continuous monitoring          | No — runs at login/VPN connect    |
| Maintenance    | Agent + descriptions must be updated | No ongoing maintenance            |
| Best for       | Continuous compliance enforcement    | Periodic checks, BYOD, VPN access |

#### DLP - Data Loss Prevention
**Monitors and blocks sensitive data from leaving the network.**

>We can deploy these in the network appliance, endpoint agent and cloud-based.
{: .prompt-tip}

#### Other known tools
SIEM, as we have just covered, Anti-Virus/Anti-malware, SNMP and NetFlow

# Summary
This chapter covers more of the security tools that can be used. But I feel like it is quite general, and it merely provides an understanding of concepts that might be relevant in the workplace. But we shall see how it goes! At least I would be able to understand the terminology used, right?

![Alt text](/assets/images/flight_view.jpeg)
Typical picture when you get the window seat.