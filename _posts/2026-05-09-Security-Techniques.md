---
title: "4.1 Security Techniques"
date: 2026-05-09 11:59:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/security_techniques.jpg
  alt: Security Techniques
---

# Introduction to Security Techniques
We have learned mitigation techniques from the big chapter on attacks and vulnerabilities, so what are we learning over here? Let us find out!

## Security Baseline
A security baseline is the minimum required security configuration for each component in an application instance.** Manufacturers provide a baseline framework for organisations to adapt to their needs.

The organisation will then create, deploy, maintain, and audit** their security baseline on an **ongoing basis**.

It is a defined set of minimum security settings that must apply to every component of an application instance:
1. Firewall rules
2. Patch levels
3. OS configurations
4. Application permissions and settings
Every deployment must include these baselines, and **any deviation needs to be identified and corrected promptly.**

#### Sources of Security Baselines
So the manufacturers that were mentioned before, which include:

|Source|What They Provide|
|---|---|
|Application developer|File permissions, app configuration settings|
|OS manufacturer (e.g. Microsoft)|OS-level security settings, group policy|
|Appliance manufacturer|Purpose-built device security settings|
|Third-party frameworks|CIS Benchmarks, DISA STIGs|

> Microsoft Security Compliance Toolkit (SCT): Microsoft’s tool for deploying Windows security baselines
{: .prompt-info}

#### Updating the baselines
We need to update the baseline when:
1. New vulnerability found
2. Application updated with changed configuration requirements
3. New OS installed, requiring a new baseline from scratch
4. Conflict between 2 manufacturers' baseline reccos

## Hardening Targets
We have learned about hardening techniques previously. Here is a quick revisit on the hardening targets that we need to focus on.

#### Mobile Devices
We need to **apply patches**, **segment** personal data from other personal data and deploy Mobile Device Management (**MDM**) that companies need. For example, not using the camera in the workplace. The device can be either **BYOD** (bring your own device) or **COPE** (Company-Owned, personal use enabled)

**MDM — Mobile Device Manager** is a centralised tool for managing all mobile devices.

| Capability                           | Example                                                        |
| ------------------------------------ | -------------------------------------------------------------- |
| Policy enforcement                   | Screen lock after inactivity, PIN requirements                 |
| Feature control                      | Disable camera inside corporate HQ                             |
| Data segmentation                    | Corporate partition separate from personal                     |
| Security updates                     | Push patches to all managed devices                            |
| BYOD the onboarding/off-the boarding | Enrol new device; wipe corporate partition when device is sold |

#### Workstations
Like the laptops. Patches, remove unneeded software and use Endpoint Detection and Response (EDR) or AV.

#### Network Infrastructure (Switches, Routers, Firewalls)
Remember to change default credentials, configure the authentication and check for patches once again.

#### Servers
Other than patches and auth, also practice least privilege and restrict bad communications.

#### Cloud Workstations
Least privilege, EDR and use backups

#### SCADA/ICS
Proper segmentation from the internet, make sure there is very limited access and have a centralised control to monitor.

#### Embedded Systems
While patches are rare, patch immediately since it is critical. Also segment and use firewall.

#### Real-Time OS
Segment, use minimum services and firewall it.

#### IoT Devices
Prioritise patches with the same reason as embedded systems and segment properly,


## Securing Wireless and Mobile
This covers securing Wi-Fi, Bluetooth, Cellular and also AP placement and channel selection.

#### Wireless Site Surveys
This is to assess the **Radio-Frequency environment** before and during the wireless network deployment.

| Activity              | Purpose                                            |
| --------------------- | -------------------------------------------------- |
| Identify existing APs | Map all SSIDs in range — yours and neighbours’     |
| Spectrum analysis     | Identify channel usage and interference sources    |
| Heat mapping          | Visualise signal strength across physical space    |
| Channel selection     | Choose channels avoiding overlap with external APs |
| Regular re-surveys    | RF environment changes — new APs appear over time  |

#### Device Ownership Models
Apart from BYOD and COPE that we just learned, there is also **CYOD** (Choose Your Own Device), which is Company Owned Employee chooses the model, so I guess I get the flexibility of which model of the phone I want compared to COPE.

#### Wireless Security Risks by Technology
**Cellular**: Traffic monitoring, location tracking (triangulate) and global exposure
**Wi-Fi**: Unencrypted public Wi-Fi, on-path attacks, passive monitoring, and even DoS
**Bluetooth**: Unauthorised access, auto-connect


## Wireless Security Settings
We will go through the change from WPA2 to WPA3 and also 802.1X with EAP, but it's exactly the same.

#### WPA2 Weaknesses
The four-way handshake is not secure due to **offline dictionary attack** and the pre-shared key (PSK) is not that hard to crack, can be done in days for weak ones and anyone with the PSK can just join the network and decrypt others' traffic.

#### WPA3

|Feature|Detail|
|---|---|
|**GCMP**|Galois Counter Mode Protocol — stronger block cipher than WPA2’s CCMP|
|**GMAC**|Galois Message Authentication Code — stronger message integrity check|
|**SAE**|Simultaneous Authentication of Equals — replaces the four-way handshake|
|**No hash over the air**|Session keys derived locally on each device — nothing to capture and brute-force|
|**Per-user session keys**|Even with shared PSK, each user gets a unique session key — can’t decrypt others’ traffic|
|**Mutual authentication**|Both client and AP authenticate each other|
|**Dragonfly handshake**|IEEE name for the SAE key exchange (based on Diffie-Hellman)|


WPA3 has 3 Authentication Modes:

|Mode|Also Called|Use Case|Auth Method|
|---|---|---|---|
|**Open**|None|No security|None|
|**WPA3-Personal**|WPA3-PSK|Home networks|Pre-shared key|
|**WPA3-Enterprise**|WPA3-802.1X|Corporate networks|Username/password via AAA server|

## Application Security
Now it is time to secure the application layer.

#### Input Validation
We make sure that data entering the application matches what we expect before processing it. This prevents:
- Buffer Overflow
- SQLi

#### Fuzzing
Automated testing that feeds **random or unexpected data** into the application inputs to see how the app handles bad input

#### Cookies
We need to make use of **HTTPS** to transmit as cookies itself provides attackers the ability to log into your session.

#### SAST — Static Application Security Testing
**Scans the source code without executing** to find vulnerabilities. It will output a list of flagged code issues with line numbers and recommendations. However, there might be false positives so the developer should review the output.

#### Code Signing
Developer have a **signing certificate** from a CA and should sign their application with their private key. When installing the app, the OS will verify the signature.

Remember that code signing can give you **Proof of Integrity and proof of Origin** but not confidentiality.

#### Sandboxing
**Isolate** the app so it can only access its necessary resources. This is so that even if app is compromised, the breach can be contained.

#### Application Monitoring
There should be **built-in logging and monitoring** to detect attacks and unusual behaviour in production. These logs are analysed with **automated tools** and can surface unknown vulnerabilities and active attacks.


# Summary
Mainly learned about security baseline, WPA3 and MDM here. Feels like it's more of an information dump here since everything is short but it's just facts. Hopefully, I can remember them hehe

![Alt text](/assets/images/shrine_gate.jpeg)
Here is a random big shrine gate.