---
title: "2.3 Types of Vulnerabilities"
date: 2026-05-04 22:15:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/vulnerability.jpg
  alt: Vulnerability
---

# Introduction
In this topic, we will be covering more about the different vulnerabilities present. Let's see if I came across all of them before!

## Memory Injection
We know that all software runs in the memory, and Malware exploits this by running as its own process or injecting itself into another legitimate process.

#### Process Injection
Malware injects itself between the start and end addresses of an already running legitimate process. This is powerful because:
1. **Evades Detection** since it is a legit process
2. **Privilege Escalation** to the host process's rights
3. **No separate process**, no new sus entry

#### DLL Injection
DLL stands for Dynamic-Link Library; it is a **reusable executable file** that multiple processes can load and use.

> Different from return-to-libc as DLL makes use of external code.
{: .prompt-warning}

The attacker places a malicious DLL on accessible storage and inserts a path to it into the target process. The target process will execute normally and load the DLL into memory. Now the DLL is running inside the legit process with its permissions.


## Buffer Overflow
Familiar topic of having an attacker write more data into a memory location than it was designed to hold, causing the excess to **spill into adjacent memory**.

As I recall, it is about having a variable-length input, and the attacker provides an input that overflows the input length, causing another memory location to be overwritten. This is hard to exploit as the attacker needs a workflow that is **repeatable, precise and advantageous.** Recall that we have Address Space Layout Randomisation (ASLR), an unexecutable stack that all make it harder 🤯.

Buffer Overflow can also be used to escalate privilege!


## Race Condition
OS concept where the application has shared resources being modified at the same time. The term **TOCTOU** is used when a value changes between when it's checked and when it's used. Over here, it seems to cover a bit more than that and is also on the fact that the application does not account for 2 events happening simultaneously.

This might not be intentional, but it can cause big problems. Even a case for **Mars Rover Spirit** (reboot loop) is considered a race condition because the error persists faster than the fix, causing a loop (fix was not implemented, fix and reboot happened simultaneously).

#### Defences Against Race Condition
As we recall, we can make use of Mutex and atomic operations to solve it from the OS coursework. We can also validate the input and use thread-safe code.


## Malicious Updates
Updates are often recommended, but we are actually taking up the **same risk as when we download applications**. Attackers can insert malicious code into the update itself to bypass defences because
- The update is from a trusted source
- digitally signed by a legit developer
- Users and systems install updates promptly
- Security tools may whitelist the update process

#### Best Practices for Safe Updates
1. Always back up before updating
2. Verify source
3. Prefer built-in update mechanisms
4. Check for digital signatures

#### Sites to download the update
Always go to the **developer's official site** to update and not random pop-ups or third-party download sites. **In-app auto updates** are highly trusted but not fully secure! Many OS only install apps **signed by a verified developer,** which provides a high level of trust, but it's not perfect!

> SolarWind Orion (Dec 2020), attackers hid malicious code in the legitimate software auto updates that are signed by SolarWinds and distributed automatically.
{: .prompt-info}

In the end, we are just having trust in the developer to be careful, so it is still possible that it is not secure.


## OS Vulnerabilities
OS is a big target as it contains so **many lines of code**, and it is a constant race between attackers and defenders patching the OS. Microsoft has **Patch Tuesdays** when they update their security patches on the second Tuesday of every month.

OS are high-value targets since compromising the OS means you have foundational access to other apps. All devices run an OS!

##### The Vulnerability Lifecycle
Unknown -> Discovered -> Reported -> Patched -> Deployed -> Closed


#### Patch Management Best Practices
1. Patch ASAP
2. Back up before patching
3. Test before production deployment
4. Verify patch source
5. Plan for reboots
6. Have a rollback plan to return to the previous known good state

We need to have more testing for the enterprise environment and have a staged rollout.

#### Types of OS Patches

| Patch type                      | Reboot required? | Notes                                                        |
| ------------------------------- | ---------------- | ------------------------------------------------------------ |
| **Background/automatic update** | Often no         | Installs silently, with minimal disruption                   |
| **Core OS/kernel patch**        | Yes              | Touches fundamental components — reboot required to activate |
| with **Application patch**      | Sometimes        | May just need the app to restart                             |


## SQL Injection
It is a code injection attack where an attacker inserts their own SQL commands into an application's input fields, causing the database to execute unintended queries.

Recap on how to attack:

```sql
SELECT * FROM users WHERE name = 'Professor' OR '1'='1'
```

Injected Input: `Professor' OR '1'='1`

This asks for everything in the database in the table. This allows you to have complete control over the data inside.

#### Defences Against SQL Injection
1. **Parameterised queries**, treat input as data and never as executable SQL
2. **Input Validation**, reject input containing possible injection characters like ''
3. **Stored Procedure** to validate
4. **Least Privilege** DB accounts can only select, not delete
5. Web Application **Firewall**, detects and blocks common SQLi patterns


## Cross-Site Scripting (XSS)
It exploits the trust that the browser has in a legit website. Exploits JavaScript.

#### High-Level Attack Workflow
1. Attacker crafts a link with a malicious script
2. Attacker delivers the link to the victim
3. Victim clicks on the link, bringing the browser to a legit, trusted site
4. Malicious Script runs from inside the browser
5. Script silently steals data (cookies, session IDs, credentials)

#### Type 1 - Reflected (Non-Persistent) XSS
Reflected attack where the **malicious script is in the URL itself**. Normally, the link is sent through a phishing email. When the victim clicks the link, the malicious script is sent to the server, the server reflects it in the response, and the victim's browser executes it.


#### Type 2 - Stored (Persistent) XSS
Attacker posts the **malicious script on 3rd party site**, normally social media, for better circulation. Script is stored on the server (different from type 1, where it is not stored anywhere). 

### Reflected vs Stored — Key Differences

|                     | Reflected (Non-Persistent) | Stored (Persistent)       |
| ------------------- | -------------------------- | ------------------------- |
| **Script location** | In the URL / crafted link  | Saved on the server       |
| **Targeting**       | Individual victim          | Anyone visiting the page  |
| **Delivery**        | Email, SMS, direct message | Posted publicly on a site |
| **Scale**           | One victim at a time       | Potentially thousands     |
| **Persistence**     | Gone after the request     | Stays until removed       |

#### Defences against XSS
Some defences: Input validation on server side, Don't click unknown links, Disable JavaScript, Have token expiration.


## Hardware Vulnerabilities
Firmware/Hardware vulnerability affects most embedded hardware devices. Manufacturers are often too lazy to update their security patches. 

#### End of Life (EOL) vs End of Service Life (EOSL)
**EOL** means **stopping the sale of the product**, but it still has security patches, while **EOSL** means the company will **stop supporting the product entirely**, no more security patches.

EOL is the warning sign for you to start switching, and EOSL suggests critical risk, and you should either:
- Pay for extended support (rare)
- Replace the device with a supported model
- Implement compensating controls if replacement is not immediately possible

#### Legacy System
Might be running EOSL software, we will need to have additional security protections, like additional firewall rules and IPS signatures for older OS.


## Virtualisation Vulnerabilities
**Unique to VM**. There are inconsistent configurations for the different VMs, and there are the same OS vulnerabilities as the host device. There are some vulnerabilities unique to VM, such as **local privilege escalations, command injections and information disclosure**.

#### VM Escape
Even though VM is designed to be a self-contained, isolated environment. However, the VM escape can break this isolation and jump to the host or move to another VM.

This will be a huge exploit!

>Pwn2Own 2017: Exploit using a JavaScript engine bug in Microsoft Edge, and can exploit the Windows 10 kernel vulnerability to gain full access to the guest OS and exploit hardware simulation in VMWare
{: .prompt-info}

A **chained sequence of attacks** that managed to escape from the VM 😮.

#### Resource Reuse
Sometimes, the hypervisors overcommit resources and VMs are allocated more than they physically can have, relying on the hypervisor to manage actual usage. This will cause sharing of memory based on actual need. This causes vulnerability where **data can leak** across VM boundaries.


## Cloud Vulnerabilities
Cloud adoption in the world is almost universal (everyone uses cloud, I should better start learning that too after Security+ hehe 😛). Sensitive data can be stored in the cloud, and we need to have the right protections for it, but 76% of organisations (according to the video) are not using MFA for cloud console users, and 63% of cloud code is unpatched. 

#### Types of attacks on Cloud:
- **Denial of Service (DoS)**
	- A fundamental attack type to make things unavailable.
- **Authentication Bypass**
	- Take advantage of weak or faulty auth, just like the lack of MFFA.
- **Directory Traversal**
	- Faulty config puts data at risk, and an attacker can navigate into unintended places
- **Remote Code Execution**
	- An attacker can exploit an unpatched app to gain remote code execution (Log4j Critical flaw in Java logging library)
- **Out-of-bounds write**
	- Attacker writes into unauthorised memory areas, which can either cause RCE or a system crash (DoS)
- **XSS**
- **SQL Injection**

Therefore, as before, remember to patch, use MFA, sanitise input, disable traversals, maintain least privilege and have cloud security posture management to detect misconfigurations.


## Supply Chain Vulnerabilities
What is the supply chain?

```
Raw materials - Supplier - Manufacturers - Distributors - Customers - Consumers
```

**3 Categories**:
1. Service Providers: direct or indirect access to target internal systems
	1. We need to have ongoing security audits built into contracts with service providers
2. Hardware (Counterfeit/Tampered): New hardware is generally trusted, but it could be tampered with or even a fake.
	1. We need to have trusted vendors, strict acquisition policies and not trust new devices until verified
3. Software/Updates: Previously mentioned
	1. Even open-source software has risk; anyone with code access can insert malicious code


## Misconfiguration Vulnerabilities
It is the easiest vulnerability to exploit since there is just an open door that the developer forgot to close.

#### Open/Unsecured Cloud Storage
Data stored without access controls can allow anyone to just come in and take it. Attackers make use of automated reconnaissance to detect **open S3 buckets** to steal data.

#### Unsecured Admin/Root accounts
Normally, when the account password is weak, or the default one is used. Having too many root accounts can also be a hazard. 

**Best Practice**: Disable direct root login, use a user account to escalate privilege. Use strong passwords

#### Cleartext/Insecure Protocols
Some protocols send **everything in Plaintext**, without encryption. Use the secure ones instead of those, so that sniffed packets will not reveal sensitive information

> Insecure Protocols: Telnet, FTP, HTTP, SMTP, IMAP, POP3

####  Default Credentials on IoT devices
Each IoT device is shipped with **default usernames and passwords**; they might not prompt for a change in password, but we should, since the default credentials are publicly searchable.

#### Open Service Ports
As previously mentioned, having more open ports means a larger attack surface, and we should **make use of firewall rules to restrict access**. Make sure to audit the firewall rulesets regularly.


## Mobile Device Vulnerabilities
Mobile devices are a lot more dangerous since they contain sensitive data, are small, portable and always connected. It might contain company-sensitive data as well. It has a **Global Attack Surface**, which means that anyone in the world can attempt to access data.

Mobile OSes restrict access to the underlying system, but **Jailbreaking** (IOS) and **Rooting** (Android) replace or bypasses that restriction. This means that all Mobile Device Management (MDM) Controls are useless, and it removes app vetting and makes your phone a lot more unsafe.

#### Sideloading
Installing apps outside the official app store. Normally, MDM makes sure that you only install from the **company app library or approved app stores**.

#### Acceptable Use Policies (AUPs)
In employee handbooks and AUPs, it is explicitly stated not to jailbreak/root/sideload for administrative, **managerial control**.


## Zero-Day Vulnerabilities
It is a security flaw that is **unknown to the software vendor**, and if an attacker discovers and **exploits it before the vendor does**, it is known as a zero-day attack.

> 'zero' actually means the number of days the vendor has had to fix it

A zero-day window is the time between exploitation and a patch.

#### Why is this dangerous?
It is more dangerous because **no patch exists,** and the **vendor is not even aware of the vulnerability**. Attackers will definitely not alert the vendor to where they found the loophole, and they can bypass all signature-based defences.

#### CVE - Common Vulnerabilities and Exposures
It is a public database of known security vulnerabilities. Each vulnerability with their own CVE ID. It is maintained at CVE.mitre.org. Once a zero-day is patched and published, it will get a CVE Entry.

This is often paired with a **CVSS** (Common Vulnerability Scoring System) to assign a severity score.

#### Defences
Since we cannot patch something we do not even know exists, we need to work on our **detection, containment, and resilience**. We should make use of sandboxing to limit the impact and also use behaviour-based detection by monitoring unusual activity.

# Summary
This chapter covers a lot of different vulnerabilities. Even though they belong in different categories, a lot of them actually are intertwined. For example, the default credentials are a common issue in some of the vulnerabilities.

I wonder if, during gap analysis, the framework that we use will cover all these different bases?

![Alt text](/assets/images/lhh_sunset.jpeg)
My view from my HKU dorm!