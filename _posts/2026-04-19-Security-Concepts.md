---
title: "1.2 Security Concepts"
date: 2026-04-19 15:22:00 +0800
categories: [Security+]
tags: [Security+]
image:
    path: assets/images/cyber_related_for_CIA.svg
    alt: Security Concepts
---

# 1.2.1 CIA Triad
There are different versions for CIA, at least from what I learn in school, they normally modify it to be **Confidentiality**, **Integrity** and *Authenticity*.

However, in the real world environment, it is actually **Availability** and not *Authenticity*.

> Just remember: Confidentiality, Integrity and Availability
{: .prompt-info }

##### Some guiding questions
C: Can the right person access this? <br>
I: Was the data tampered with? <br>
A: Can people access it when they need it? <br>

---

## Confidentiality
We ensure that the data is only accessible to **authorised individuals**.

This can be done via:
1. **Encryption**: makes data unreadable to interceptors
2. **Access Controls**: Limit who can view or modify specific data
3. **MFA**: Extra proof to ensure that you have the access (this is a method to enforce access control)


## Integrity
We ensure that the data arrives exactly as it was sent, **untampered**.

This can be done via:
1. **Hashing**: Cryptographic hash sent alongside data so receiver can verify
2. **Digital Signature**: Proves both integrity and origin

> *Digital Signature* is to proof integrity and origin while *Certificates* are to prove identity
{: .prompt-info}

## Availability
We ensure that the systems and data are **accessible** when needed.

This can be done via:
1. **Fault Tolerance**: Even if one component fails, other components can continue
2. **Redundancy**: Duplicate systems or data paths
3. **Patching**: Keep systems stable and closes exploitable vulnerabilities.

## Conclusion
Rather simple concept that was learned previously. Learned some new stuff about Availability since it is often removed from Cybersecurity Modules. 🤔

---

# 1.2.2 Non-Repudiation
Familiar concept from all the Cybersecurity courses that I have taken up till now. Sender cannot deny having sent a message. It provides both **Proof of Integrity** and **Proof of Origin**.

<br>

Proof of Integrity can be shown using Hashing while Proof of Origin can be shown using Digital Signature.

---

## Hashing as a Proof of Integrity
Hashing takes an *arbitrary sized input* and return a *fixed size digest*.

#### Properties:
1. **Pre-Image Resistance**: Unable to retrieve x easily given H(x)
2. **Collision Resistant**: Unable to find another x' != x s.t. H(x) = H(x')
3. **2nd Preimage Resistance**: Unable to find another x' != x1, where x1 is a specific input s.t. H(x') = H(x1)

> Any change to the input will produce a completely different hash
{: .prompt-tip}

> Hashing alone can only confirm data integrity but not identify who sent it which is why we need the second part, Proof of Origin
{: .prompt-warning}


## Digital Signature as Proof of Origin
Making sure that you are talking to the right person (Bob?) with PKC (asymmetric encryption with public private key pair).

### Sequence
1. Alice encrypts plaintext with private key producing the digital signature
2. Alice sends both plaintext and digital signature to Bob
3. Bob decrypts using Alice's public key and then compare it with the plaintext

> The only way to decrypt successfully and be verified is to have Alice's private key
{: .prompt-tip}

## Combining both Hash and Digital Signature
1. Alice hashes plaintext into digest
2. Alice encrypts digest with private key to give digital signature
3. Alice sends Bob both the digital signature and the plaintext
4. Bob decrypts the digital signature to obtain digest
5. Bob hashes the plaintext and compare if it is the same as the decrypted digest

With this, **Integrity** and **Origin** is confirmed.


### Certificates
Certificates ensure that the public key indeed belongs to Alice. This is done by having a **Certificate Authority** signing the entire certificate that contains:
1. Alice's public key
2. Alice's identity information (name, organisation, domain etc.)
3. Validity period
4. Other metadata

CA will sign with its private key and CA is actually signed by another CA all the way up to the Root CA that is set to be trustable in hardware (at least from what I know 🤓).

## Conclusion
Non-Repudiation requires both Integrity and Origin.

![Alt text](/assets/images/siamese_yes_cat.png)

---

# 1.2.3 AAA Framework
It is the first time I have heard of this Framework and it stands for:
**Authentication, Authorisation and Accounting**

#### What do they mean?
**Authentication**: Prove who you are <br>
**Authorisation**: What you can access <br>
**Accounting**: Log what you did <br>

---

## Authentication
We start with Identification and then Verification

It is split into 3 different factor types:
1. Something you know (password)
2. Something you have (smart card)
3. Something you are (biometrics)

### Device Authentication via Certificates
Since devices cannot type passwords, we make use of digital certificate that is installed on the device

If you recall from the previous post about CA, certificate is signed by the CA and during login, this certifcate will be verified. Certificates are used in VPN concentrators and endpoint management systems.

#### CA Flow
1. CA creates and digitally sign a certificate for the laptop
2. Certificate installed on laptop
3. During Auth, device presents cert
4. Verifier checks if it is signed by trusted CA


## Authorisation
After Auth, the system will now check what resources can the device/user can access

### The Problem: Scaling
Without a authorisation model, every single user will need individual rights manually assigned to every resource. The admin is gonna cry 😭.

### The Solution: Abstractions
As we know, we always solve things using abstractions in CS and tada we have it here again.

3 Models:
1. **Role-Based**: User assigned to roles and each role has their own permissions
2. **Attribute-Based**: Access based on the user attributes (department, location, time)
3. **Organisation-based**: Access is defined by organisation structure

> Roles are more dynamic and flexible than Positions (organisation) since positions are static
{: .prompt-info}


## Accounting
We have to log down everything for **Audit** and **Forensic** purposes.
- Login Timestamp
- Data sent and received
- Logout Timestamp
- Actions performed

This provides an audit trail and can prove what happened during an incident

## Putting everything together with an example,
For a VPN Login Flow:
1. Client connects to VPN Concentrator
2. Concentrator prompts for credentials
3. Client sends username and password
4. Concentrator forwards to AAA Server
5. AAA Server checks credentials against database
6. If there is a match, sends approval back to Concentrator
7. Concentrator grants access to internal resources

![Alt text](/assets/images/adorable-cat-checking-mailbox-with-love-hearts_1183781-2429.avif)

---

# 1.2.4 Gap Analysis
It is a study of assessing of how secure you are right now and how secure you want to be in the future. You will produce a detailed report with a roadmap to close the identified gaps.

## Core Concept

| Concept       | Description                                                    |
|---------------|----------------------------------------------------------------|
| Current State | What security controls, processes and people you have today    |
| Target State  | The goal you are working towards (e.g. NIST, ISO 27001)        |
| Gap           | The difference between current and target state                |
| Report        | Documents the gap and a roadmap of how to close it             |

## Procedure for Gap Analysis

### Step 1 - Choose a Baseline
A **baseline** is something for us to measure against. There are some common ones that I do see JDs include such as ISO/IEC 27000-series of standards (for EY).

### Step 2 - Evaluate People and Processes

#### People Evaluation
We are evaluating people's:
- Formal experience in IT security
- Training received
- Knowledge of existing security policies and procedures

#### Process Evaluation
We are evaluating systems and processes:
- Review existing IT system against formal security policy documentation
- Identify weaknesses in current systems
- Compare weaknesses against best-practice compensating controls (how well we mitigate the weakness)


### Step 3 - Break down Broad Categories
Start with broad security domains, and then drill into individual controls.

We make use of a broad requirement and then the controls we have to satisfy that requirement.

| Broad Requirement                       | Individual Controls                         |
|-----------------------------------------|---------------------------------------------|
| Limit system access to authorised users | User Registration and Deregistration        |
|                                         | User access provisioning                    |
|                                         | Management of privileged access rights      |
|                                         | Review of user access rights                |

The same thing here is done across **ALL DOMAINS, ALL DEVICES, ALL LOCATIONS**. That's actually kinda heavy workload man, how long do they even take?

> For a 50-250 employees organisation with framework ISO 27001 it is estimated to take 4-8 weeks according to snapgrc's website
{: .prompt-info}

たいへんですね！

### Step 4 - Create the Gap Analysis Report
Now it is time to generate the report.

What to include:
1. Current State for each baseline objective
2. Target State for each baseline objective
3. Gap between Current and Target states
4. A roadmap on how to close each gap
5. All recommendations to meet the baseline

> The roadmap consists of time, money, equipment and change control
{: .prompt-info}

### Common Way to Present Findings: Traffic Light

| Colour       | Meaning                       |
|--------------|-------------------------------|
| 🟢 Green  | Close to meeting baseline    |
| 🟡 Yellow | Partially meeting baseline   |
| 🔴 Red    | Significantly below baseline |

## Final Thoughts
Will this be what GRC people do daily? I am inclined in going to consultancy firms for their global outreach so will I be looking at this alot in the future? 🤔

![Alt text](/assets/images/cat_thinking.jpg)

---

# 1.2.5 Zero Trust Architecture
Nothing is trusted on the network by default. This requires every device, process and user to prove itself every time it wants to access a resource.

It so troublesome but I guess its a tradeoff for security since you are not having a chain of trust like how CAs work.

## Specifically, why zero trust?
Traditionally, once something is past the firewall, the inside is relatively open and now anything can run freely inside (even Malware 😈)

But by having zero trust, you need to authenticate at every step and so this restriction will keep checking for malicious intent.

![Alt text](/assets/images/cat_clenching_fist.jpg)

## Planes of Operation
Every security device, whether it is physical, virtual or cloud, is split into 2 functional planes:
1. Data Plane: Process traffic in real time
2. Control Plane: Manages and configures data plane

> Data Plane does the work while Control Plane configures the settings to do the work
{: .prompt-info}

## Adaptive Identity
It increases the security by checking for extra context to authenticate on top of password and username, for example:
- Source IP
- Relationship to Organisation
- Type of Connection
- Time of access

## Limiting Entry Points
By reducing the attack surface by only allowing access through controlled paths, it is easier to defend.

## Policy-Driven Access Control
All the adaptive identity data points feed into a policy engine that decides whether to:
1. Allow
2. Deny
3. Revoke

## Security Zones
Instead of having a user to server relationship, we split it into various zones for the whole path of the connection.

| Zone              | Description                  |
|-------------------|------------------------------|
| Untrusted         | External/Internet facing     |
| Trusted           | Corporate Office Users       |
| Internal          | Data centres/servers         |
| VPN/Dept segments | Granular sub-zones per team  |

With these zones, rules can be set such as whether going from a zone to another is denied by default or implicitly trusted.


## The Policy Framework (PEP/PDP)
There are 3 components that will enforce decisions.

### Policy Enforcement Point (PEP)
This is the gatekeeper where all traffic passes through it. However, it **DOES NOT make decisions by itself**. It gathers the traffic and passes it to the Policy Decision Point (PDP)


### Policy Engine
Examines each request against pre-defined security practices and then make the decision to: **grant, deny or revoke**.


### Policy Administrator
It takes the Policy Engine's decision and send it back to PEP. It creates and delivers access tokens or credentials if access is granted.


> **PDP** is the combination of policy engine and policy administrator
{: .prompt-info}

![Alt text](/assets/images/zero_trust_diagram.png)
Image from Professor Messer's Youtube Video on Zero Trust Architecture!


## Overall Zero Trust Flow
Untrusted -> Data Plane -> PEP -> Policy Admin -> Policy Engine -> Policy Admin -(if granted)-> goes into Trusted zone and access resource.

## Final Thoughts
Sounds like at every single checkpoint, I will have a security guard A (PEP) pass my ID to security guard B (PDP) who will check my ID and ask me some questions before letting me in.

Reminds me of my trips from HK to ShenZhen. I MISS EXCHANGE UEUEUEUEUUEUE

![Alt text](/assets/images/cat_crying_with_bread.gif)

---

# 1.2.6 Physical Security
Security does not only happen in the digital world, it happens in the real world as well!

Physical security controls protect facilities, assets and people from unauthorised physical access.

As we recall from Security Controls, there are multiple control categories and we might be able to classify the physical security measures into them!

![Alt text](/assets/images/cat_loading.jpg)

---
## Perimeter Controls

### Bollards / Barricades
Something that blocks access using barricades (duh), normally brightly coloured as a security notice.

### Fencing
Could be transparent or opaque, it is obvious by design to be a **deterrent**.

### Lighting
It is hard to believe that lighting also falls under perimeter controls actually, but it eliminates dark areas where unauthorised access is easier. It works with infrared cameras for night time coverage.

> Depending on the exact implementations, it could either be preventive, deterrent or detective.
{: .prompt-warning}

---
## Entry Controls

### Access Control Vestibule (Mantrap)
It is a room between 2 secured doors. The mantrap is essentially an airlock for people. You're stuck in the middle room until the system decides you're allowed through. There are 3 configurations of how it can work.

| Configuration     | How it Works                                              |
| ----------------- | --------------------------------------------------------- |
| Unlocked Doors    | Interlocked — one opens, the other locks                  |
| All Locked        | Badge door 1 → closes behind you → door 2 unlocks         |
| One Always Locked | One door always requires active authentication to open    |

#### More detailed explanation of Configurations:

**Unlocked Doors** <br>
Both doors work normally but are interlocked — if one opens, the other locks. So you can never have both open at the same time. This prevents someone from tailgating through both doors in one rush.

**All Locked** <br>
Both doors are locked by default. You badge/authenticate at door 1, it opens, you walk in. Door 1 closes and locks behind you. Only then can door 2 open. One person, one entry, fully controlled.

**One Always Locked** <br>
One door is permanently locked and never opens on its own — you always need active authentication to pass through it. The other door may be more freely accessible. Think of it as a one-way strict checkpoint.

### Identification Badges
It must be worn visibly at all times and it should contain photo, name and role details. This is integrated with electronic locks so that you can tap in rooms.

---
## Surveillance Controls

### CCTV (Closed Circuit Television)
I think its my first time seeing the full form for CCTV. Basically it is about having multiple cameras networked together and feeding into one central storage point.

There are more features to the cameras now such as motion detection, facial recognition etc.

### Security Guards
Of course we need to have security guards in Physical Security. They validate employees and guests at entry and often operate in pairs (*Two-Person Integrity/Control*).

> Two person shifts so that it prevents one guard from circumventing security policy alone and provides checks and balances
{: .prompt-info}

### Detection Technologies
Remember the waves that we have learned in pre-uni, its back.

| Technology         | How it works                                                           | Best for                                                 |
|--------------------|------------------------------------------------------------------------|----------------------------------------------------------|
| **Infrared**       | Detects infrared radiation — works in light and dark                   | Motion detection, limited area                           |
| **Pressure sensors** | Detects change in force as something passes over                     | Floor-level intrusion detection                          |
| **Microwave**      | Detects movement over a large area                                     | Wide open spaces, larger zones                           |
| **Ultrasonic**     | Sends ultrasonic signals, detects reflected sound waves                | Motion detection + collision detection (e.g. loading zones) |

## Final Thoughts
That is quite a lot of content for physical security, cant imagine how much will be in place for security in the digital world. But yea physical security is definitely needed in the real world since its also a viable attack option. (I mean if I can sneak in and access ur laptop, Im trusted by ur digital defences right? 😈 悪いですね)

![Alt text](/assets/images/cat_shocked.jpg)

---

# 1.2.7 Deception and Disruption
So why did I put a honeypot as the thumbnail? Because security professionals can actively deceive and disrupt attackers using fake systems, files and data to **waste the attackers' time while gathering intel on their techniques**!

The 4 things that defenders use:
1. Honeypot
2. Honeynet
3. Honeyfile
4. Honeytoken

---
## Honeypots
It is a **Virtual World** that is designed to attract (normally automated) attackers away from production systems.

The goal is to observe what attack techniques were used.

They can be built using commercial or open-source software and it is an **Arms Race** since attackers will try to improve at identifying honeypots while honeypots try to be more realistic.

## Honeynets
**Multiple honeypots together** form a full fake infrastructure. It might contain more devices like workstations, servers, routers and firewalls. This makes it alot more believable than a single honeypot. This *keeps attackers busy for a longer time* and *reveals more sophisticated attack chains*.

## Honeyfiles
**Files that contain fake but convincing information**. These are normally named to look valuable, e.g. passwords.txt. No legitimate user should ever have access to these files. An alarm/alert is triggered the moment someone opens or views the file.

## Honeytokens
These are traceable pieces of fake data seeded in the systems or public areas. If the data appears elsewhere on the internet, we will know that it has been hacked.

Some examples of such tokens:

| Type                      | How it works                                                        |
|---------------------------|---------------------------------------------------------------------|
| **Fake API credentials**  | Posted to a public cloud share — non-functional, but tracked        |
| **Fake email addresses**  | Monitored — if they appear online, someone leaked your data         |
| **Fake database records** | Seeded in a DB — if records appear externally, the source is identified |
| **Browser cookies**       | Tracked cookies that reveal if data was exfiltrated via browser     |
| **Web pixels**            | Tracking pixels embedded in documents — ping back when opened       |

## Final Thoughts
This is a rather short chapter but I guess the beauty of this is it really helps with detection and also identifying what actual attackers are aiming for at our systems. A useful tool but it was mentioned that it is an arms race, so I wonder how sophisticated the automated attackers are.

![Alt text](/assets/images/cat_shoushoubaazu.jpg)
