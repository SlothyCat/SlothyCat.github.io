---
title: "2.4 Malicious Activity"
date: 2026-05-06 16:15:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/malicious_activity.jpg
  alt: Malicious Activity
---

# Introduction

We will be covering more on the actual attacks now, after we have explored the various vulnerabilities in the previous chapter!

## An Overview of Malware

Malware is malicious software that is designed to harm, exploit, or steal from a system or its user. It normally requires a combination of multiple Malware to complete an attack.

#### How does Malware get in?

Malware usually gets in through a malicious link, or downloads whether it is clicked or automated. Worms in particular do not even need user action and will self-install across systems.

Rough workflow of Malware:
```
Worm exploits OS vulnerability
        ↓
Installs itself on storage
        ↓
Installs backdoor/remote access malware
        ↓
Attacker connects via backdoor
        ↓
Installs additional malware (keylogger, ransomware, botnet agent)
```

#### Ransomware
It is one of the **most impactful and commercially successful** malware types, where it **encrypts your personal data** but allows your OS to work as usual. The payment method to retrieve the decryption key is untraceable (maybe Cryptocurrency).

We can make use of **offline backups** as defences and **always update** OS, Apps and Antivirus. Antivirus has a list of signatures to recognise and block known ransomware before execution.

Our data has value to attackers since we are willing to pay to recover it or even face identity fraud or the leaking of sensitive data.

#### Drive-By Downloads
We do not even need to explicitly click download since Malware can be automatically downloaded when visiting a compromised or malicious website. It is rare but still occurring, so we need to remember to keep the browser and plugins updated.

#### Anti-Virus
Anti-Virus is useful in identifying malicious code using signatures (known patterns of malicious code). However, it cannot catch zero-day vulnerabilities. It works best as one later in a defence-in-depth strategy.


## Viruses and Worms
Viruses are malware that require human intervention to execute and can take many forms apart from .exe. However, Worms can self-replicate without human intervention through the network. While both can cause significant damage, Worms are scarier since they spread faster.

#### Types of Viruses

| Type                           | How it works                                                              | Key trait                           |
| ------------------------------ | ------------------------------------------------------------------------- | ----------------------------------- |
| **Program / Executable virus** | Attaches to or replaces an executable — runs when the program is launched | Most common mental model of a virus |
| **Boot sector virus**          | Installs in the boot sector — runs automatically when the system boots    | Executes before the OS loads        |
| **Script virus**               | Embedded in browser, OS, or application scripts                           | Runs when the script is executed    |
| **Macro virus**                | Written in macro language (e.g. VBA in Microsoft Office)                  | Runs when the document is opened    |
| **Fileless virus**             | Never writes to disk — runs entirely in memory                            | Evades signature-based AV           |

#### Fileless Virus
The virus runs code directly in memory with nothing written to disk. It can, for example, run PowerShell and do stuff. To survive reboots, it might add itself to the autostart entry in the Windows Registry.

#### Worms
Once again, it is fully autonomous, spreads at network speed and can attack at any time. We can make use of firewalls, Intrusion Prevention System (IPS) and also Patch Management to defend.

|                                 | Virus                             | Worm                      |
| ------------------------------- | --------------------------------- | ------------------------- |
| **User interaction required?**  | Yes — must be triggered           | No — fully autonomous     |
| **Propagation method**          | File system, email, shared drives | Network vulnerabilities   |
| **Speed of spread**             | Limited by user actions           | Network speed — very fast |
| **Example**                     | Macro virus in Word doc           | WannaCry                  |

## Spyware & Bloatware
Spyware secretly monitors user activity and data, while Bloatware is the extra application that you see on your device installed when you first receive it. It is normally unwanted and provides security risk.

#### Spyware
Monitors everything on the infected system and sends the collected data back to the attacker's servers. Operates silently, so the victim often has no idea. 

It is normally installed through:
- P2P software bundles
- Fake Security Software
- Malicious link

It is embedded deeply in the OS; some versions do not have an obvious uninstall option. It is best to just restore from a known good backup. We can make use of MalwareBytes to find and remove spyware and other malware or other anti-malware software.

> A keylogger is an example that records every keystroke
{: .prompt-info}

#### Bloatware
Pre-installed software that manufacturers are paid to install. The security concern is just having an extra thing to worry about, and we can choose to remove them by:
1. OS app manager
2. App's own uninstaller
3. 3rd Party uninstaller


## Logic Bombs and Rootkits
There are more malware types covered here, apart from the Keylogger.

#### Logic Bombs
These are malicious code that lies dormant until a specific condition has been met, and then the payload will be executed.

The trigger types:
1. Time
2. User event (login)
3. File event
4. System state

It is hard to detect because these are **highly customised**, and no antivirus signature will exist yet. These will **sit quietly until triggered**.

We can try to detect it through **file integrity monitoring** to check whether OS files have been modified unauthorised, adhere to **least privilege,** and ensure **proper access control** so no one can just plant the bomb.


#### Rootkits
It is malware that **hides itself in the OS kernel**. These are hard to find by Anti-virus, and since they live in the kernel, it is invisible while having full system access. It does not even appear in the process list.

If you do know that you are under the attack of a Rootkit, you can:
1. Standalone rootkit removal tools - these are specific
2. Secure Boot - checks the OS kernel signature before booting to prevent a modified kernel
3. bootable scanner - scans the drive from the outside


## Physical Attacks
Who said you should only go digital? 

#### Brute Force Physical Access
This is just brute forcing physical barriers, like breaking doors and windows. 

#### RFID Cloning
Radio Frequency Identification is the technology behind most modern access badges and key fobs. And these can be cloned with a **duplicator** by bringing it near the RFID, and then you will be able to create a duplicate card for access.

So, always use **MFA** since RFID Cloning can only clone something you have.

#### Environmental Attacks
Instead of targeting systems directly, you can target the environment that the system depends on:
1. **Power** attacks - cut power to the data centre
2. **HVAC** attacks - Heater, Ventilation, Air Conditioning by making systems overheat
3. **Fire** Suppression attacks - forces DoS


## Denial of Service (DoS) & Distributed DoS (DDoS)
**DoS** forces a service offline (break A in CIA Triad) by overwhelming it or by exploiting a vulnerability. A **DDoS** makes use of thousands of compromised devices (forming a **botnet**) and then makes small amounts of traffic, producing massive floods at the target.

#### DoS
It can be **intentional or even accidental**, like having a loop, downloading a large file (overwhelming the bandwidth) and environmental accidents (water pipe breaking)

#### DDoS
Makes use of a botnet under the attacker's control via a Command and Control **(C2) server.**

**Amplification/Reflection Attacks**: The attacker can use open internet services to amplify small traffic into massive floods. Protocols that are normally abused for amplification: DNS, NTP, ICMP
 
| |DoS|DDoS|
|---|---|---|
|**Source**|Single device/attacker|Many devices worldwide|
|**Scale**|Limited by one connection|Scales to massive bandwidth|
|**Blocking**|Relatively easy (block one IP)|Very hard (thousands of IPs)|
|**Control**|Attacker operates directly|Attacker uses botnet + C2|

## DNS Attacks

#### DNS Poisoning
DNS Poisoning redirects users to a malicious IP by corrupting DNS records either on
- **DNS server**
	- Gain access to a DNS server with a known vulnerability
- **Client's host file**
	- requires access to the client device and elevated privileges
- **Intercept DNS queries in transit**
	- On-Path attack intercepting DNS queries in real time (MITM)
- **Domain Registration Compromise**
	- Attackers gain access to the domain registrar account, affecting global users

#### URL Hijiacking
**Typosquatting**: Register for a domain very similar to the legit one to catch users who mistype URLs. Attackers can either display ads, use as ransom, redirect to a competitor or deliver malware

We can make use of **DNSSEC** to digitally sign DNS records, use **MFA** and check URLs properly!


## Wireless Attacks
**802.11 management frames** are control messages sent between devices and access points to manage the wireless connection. These used to be sent in the clear, in plaintext.


#### Attack Type 1: Wireless Deauthentication
An attacker can forge deauth frames and send them to the victim device, letting it disconnect from the access point.

```
airodump-ng scans 
for APs and connected client MACs.
aireplay-ng -0 
sends deauth frames.
```

The fix was to come up with **Protected Management Frames**, incorprated to neweres standards where deauthentication, disassociation and channel switch are encrypted.

#### Attack Type 2: RF (Radio Frequency) Jamming
Flood the wireless frequency with interference, degrading the signal-to-noise ratio until communication is impossible. Jamming methods include:
- Constant signal
- Random data flood
- Legitimate frame flood
- Reactive jamming

You might also notice that your **microwave oven and fluorescent lights** might jam your RF, too.

Use a **Fox Hunt** to locate a jammer. It has a `directional antenna` to point to the source, and `attenuators` to decrease signal strength for better determination of direction.


## On-Path Attacks
AKA MITM that I have learned before. Over here, we will learn about ARP Poisoning (network-level) and on-path browser attack (device-level)

#### ARP Poisoning
We know that ARP basically is the resolution for IP to MAC address, and there is no authentication, which means that any device can send an ARP reply at any time, and it will be trusted.

An attacker can pretend to be a victim from the router's POV and the router from the victim's POV, and it will be able to read all the traffic, modify data and drop traffic.

#### On-Path Browser Attack
The attacker sits inside the victim's own device. It is used to wait for the victim to enter important information like bank details and capture these before encryption. 

Even if HTTPS is used, the malware captures data before it is encrypted and after it is decrypted.

|                             | ARP Poisoning                  | On-Path Browser                        |
| --------------------------- | ------------------------------ | -------------------------------------- |
| **Attack location**         | Network (between devices)      | On the victim's device                 |
| **Requires network access** | Yes — same subnet              | No                                     |
| **Bypasses HTTPS?**         | No (data still encrypted)      | Yes — captures before/after encryption |
| **Installation needed**     | No — pure network manipulation | Yes — malware must be installed        |
| **Victim awareness**        | None                           | None                                   |

## Replay Attacks & Session Hijacking
It captures a legit network and replays it later to impersonate the victim. The server will see the valid data and grant access.

#### Attack Type 1: Pass-the-Hash
Instead of cracking the password, the attacker can simply replay the password hash itself to authenticate.

This can be prevented by encryption and making use of salted hashes, and then having the server reject duplicate hashes.

#### Attack Type 2: Session Hijacking (SideJacking)
Browsers make use of session IDs stored in their cookies to maintain their session, and having this stolen means that the attacker can log into your session.

The attacker can make use of packet capturing, XSS, header modification and browser extensions to capture your session key, which is why you need HTTPS, VPN and short session ID expiry.

## Application Attacks
Makes use of a lot of things that we have learned before, like SQL Injection, Buffer Overflow, Replay attack, Privilege Escalation and Directory Traversal. There is something new that I will put here.

#### Cross-Site Request Forgery CSRF
aka XSRF (sea surf), one-click attack and session riding.

Basically, the attacker will trick the user's already authenticated browser to make an unauthorised request to the trusted server on the attacker's behalf.

So, the victim logs in, clicks on the attacker's malicious link, and the browser sends the request to the bank. 

This happens behind the scenes, and the victim cannot see it happening

**Anti-Forgery Tokens**: Server will include a unique cryptographic token per form/request, and it is tied to the user's session and will change with each request. This means that the attacker's forged request will not have the right token and will be rejected.

#### Client Side vs Server Side

|                      | Client-side                      | Server-side                                        |
| -------------------- | -------------------------------- | -------------------------------------------------- |
| **Runs on**          | Victim's browser                 | Web server                                         |
| **Languages**        | HTML, JavaScript                 | PHP, Python, Java, etc.                            |
| **Visible to user?** | Yes (view source)                | No                                                 |
| **Examples**         | Rendering pages, form validation | Processing requests, DB queries and fund transfers |
| **Attack surface**   | XSS, CSRF                        | SQLi, server-side injection                        |

## Cryptographic Attacks
These attacks either target the algorithm itself or target the implementation of the cryptography. We will cover our familiar Birthday Attack and also a new topic on the downgrade attack.

#### Birthday Attack
For a class of 23 students, the probability of having any 2 students having the same birthday is 50%. Kinda high if you just look at it.

This means that collisions for hash are easier than they actually are. To resolve this, we normally make use of a larger hash output size and avoid broken hashes like MD5.

#### Downgrade Attack
It forces 2 communicating devices to use a weaker encryption algorithm or no encryption at all.

**SSL Stripping**: an on-path attack that strips HTTPS and leaves only HTTP for the victim.


## Password Attacks
We should never store our passwords in plaintext and should simply hash them. Even encryption is less safe since if the key is obtained, it can be decrypted. Hashing can only be compared by brute force.

#### Password Spraying
Since most systems will lock the system after a few failed attempts, attackers can try some commonly used passwords against many accounts and not trigger a lockout and have no alarms

#### Offline Brute Force
This is even stronger than the previous, since there is no lockout, and you can have unlimited attempts. And so you can slowly brute force hashes until you find the password that outputs the same hash


# Indicators of Compromise (IOC)
I placed this in a separate section because I feel like this is not really about the attacks anymore, but the detection of the attack.

There are a bunch over here, but quite self-explanatory:
1. Unexpected Account Lockouts
2. Concurrent/Impossible logins from different locations
3. Blocked Security Updates (by malware)
4. Resource Consumption Spikes that are unusual
5. Resource Inaccessibility (might have crashed from malicious code or ransomware)
6. Out-of-cycle or missing logs
7. Unexpected company data on the internet (already leaked)
8. DNS/File modification


# Summary
That was SOOOO MANY ATTACKS. I'm tired, I feel like I got attacked.

![Alt Text](/assets/images/guangzhou_church.jpeg)
A picture from my Guang Zhou Trip!