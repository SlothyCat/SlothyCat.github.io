---
title: "4.8 Incident Response"
date: 2026-05-17 11:00:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/incident_response.svg
  alt: Incident Response
---

# Introduction to Incident Response
I believe the work here is more related to the Blue Team SOC analyst? But I could be wrong! I want to try the TryHackMe lessons for Blue Team SOC HMM

## Incident Response
Incident Response normally follows an SOP, and it can be based on NIST SP 800-61 Rev2. It involves Preparation → Detection & Analysis → Containment → Eradication & Recovery → Post-Incident.

#### Preparation
We need to be prepared for possible attacks by having an incident go bag.

**Incident Go Bag Contents**
- Laptops with specialised forensic software
- Removable media (for copying items between systems)
- Digital imaging equipment (photos and video documentation)
- Network diagrams and server documentation
- Security baselines and **file hashes of critical files**
- Known-good OS images and application images
- Policies and procedures everyone must follow

We also need to have a proper communication plan so that the stakeholders will be notified and there are defined escalation paths.

#### Detection & Analysis
Detection is not always easy, as it is **hard to differentiate between scripted background noise from legitimate breach**.

There are multiple Detection Sources that we can analyse:

|Detection Source|What It Reveals|
|---|---|
|IPS alerts|Buffer overflow attempts, exploit signatures|
|AV reports|Malware installed on a workstation|
|Configuration change alerts|Attacker modifying security settings|
|Traffic volume spike|Data exfiltration in progress|
|Web server logs|Vulnerability scanning activity against your server|
|Attacker contact|Rare but occurs — ransom demands, etc.|

#### Containment
**Stops the attack immediately** and does not wait to observe what the attacker might do next. A sandbox is an isolated environment where you can run malware and observe its effects safely.

> Some malware will detect the sandbox and delete itself rather than executing normally.
{: .prompt-info}

#### Eradication and Recovery

|Task|Method|
|---|---|
|Remove malware|Delete or quarantine; or full reimage of the system|
|Disable breached/attacker-created accounts|Prevent re-entry|
|Patch the vulnerability|Fix the initial entry point so the attacker can't return the same way|
|Restore data|Use known-good backups or original installation media|

We need to replace compromised files and lock everything down so that the attacker cannot get back in.


#### Post-Incident Meeting
This should be done ASAP after resolution to have better memory retention while events are fresh. These meetings can help improve the incident response plan for next time.


## Incident Planning
We should test ourselves before an actual event. While we are testing, we should make use of a specific scenario and use well-defined rules of engagement. We should evaluate the response and see if we need to have any changes.

#### Incident Response Testing Methods

|Method|What It Tests|Cost/Effort|
|---|---|---|
|**Tabletop exercise**|Policies and procedures (discussion only)|Low — no systems affected|
|**Simulation**|Real systems, real people, real automated defences|Medium-High|
|**Full-scale drill**|Everything — full disaster recovery activation|Highest|

**Phishing Simulation** 
1. Security team crafts a realistic phishing email (e.g. requesting a link click to update information)
2. Sends to all employees
3. Monitors: Did automated email filters block it before delivery?
4. Tracks: who clicked the link
5. Evaluates: Did anti-phishing systems block the malicious landing page when users clicked?
6. Outcome: report on click rates + assign additional security awareness training to users who clicked

#### Root Cause Analysis
This is to determine the ultimate cause of an incident.
- Review log files, files planted by the attacker, and network captures
- Reconstruct the full attack timeline from beginning to end
- **Multiple root causes are common** — a single breach often requires several security failures in sequence
- Address all root causes to prevent repeat incidents
- Distinguish between symptoms (what happened) and causes (why it was possible)

> Fixing only the symptoms will lead to technical debt
{: .prompt-warning}


#### Threat Hunting
We should **find the vulnerability first before the attackers**. Intelligence Data is reactive; you will not know the attack until it happens. It helps us speed up our reaction time using automation tools to alert us.

| Activity              | Example                                                                          |
| --------------------- | -------------------------------------------------------------------------------- |
| Review firewall rules | Find misconfigured or overly permissive rules                                    |
| Track recent CVEs     | Identify which announced vulnerabilities affect your systems                     |
| Patch status check    | Confirm all systems have the latest updates                                      |
| Monitoring review     | Ensure the right data sources are being watched                                  |
| Automated tooling     | Automated systems detect and block threats even when no one is actively watching |

## Digital Forensics
Digital Forensics is about collecting evidence so that it can remain admissible in legal proceedings in the future.

#### Legal Hold
This is initiated by a **lawyer or legal entity**, and is sent to the **data custodian**. This specifies exactly **what data must be preserved and how much**. The data is moved to a separate **ESI** (Electronically Stored Information) repository. 

Data might be formatted before storage. The custodian is responsible for safe preservation until the court requests it.

#### Chain of Custody
This ensures that the integrity and accountability are maintained throughout the forensics process

| Physical World                   | Digital World                                            |
| -------------------------------- | -------------------------------------------------------- |
| Evidence in sealed bag           | Data protected with hashes and digital signatures        |
| Signature on bag for each access | Access logs recording who accessed data and when         |
| Tamper-evident seal              | Hash comparison confirms data unchanged since collection |

> If the chain is broken or unverifiable, evidence may be **inadmissible** in court
{: .prompt-warning}

#### Data Acquisition Sources
There are multiple sources of data which include: Disk, Memory, Firmware, File system, Network devices, VM and non-obvious locations like recycle bin, bookmarks, etc.

**Live acquisition:** Some systems auto-encrypt on shutdown — capture data while the system is still running to avoid losing access to it.

**Mobile devices:** Can be remotely wiped — isolate and copy immediately, then work from the copy.

#### Forensic Reporting Structure
1. Summary/Overview
2. Detailed acquisition log
3. Integrity documentation
4. Data Analysis
5. Conclusion

#### Preservation
Handles evidence by **isolating and protecting the data**. **Working from copies** and following best practices to **ensure the admissibility of data** in court.

#### E-Discovery
This is the process of **collecting, preparing, reviewing, interpreting and producing legal documents for legal proceedings**. 

This **does not require analysis** but requires the correct format acquisition. Normally is an E-discovery acquisition and forensics analysis.

# Summary
We learned a bit more about incident response and how forensics are important, and how we keep them for legal proceedings. It is important to think about how we react when we get breached and see if we have a standard set of procedures to follow in such an event. This should be an ongoing improvement plan as well.

![alt text](/assets/images/hongliandong.jpeg)
Also a night view in Chong Qing!