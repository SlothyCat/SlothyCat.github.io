---
title: "Threat Vectors And Attack Surfaces"
date: 2026-05-04 22:15:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/security_breach.jpg
  alt: Threat Vectors And Attack Surfaces
---

# Introduction
In this chapter, we will learn more about the different ways attackers can attack systems.

## Common Threat Vectors
A threat vector is the method an attacker uses to gain access to your systems.

#### Messaging
Phishing emails, SMS and direct messages. This works as attacker impersonates a known brand
or contact to make you click into it! Very common that every one should come across.

#### Image-Based Attacks
SVG (Scalable Vector Graphics) are XML files that describe an image. Attacker can embed Javascript
within the XML file to execute, normally for Cross Site Scripting Attack. Damn, I did'nt know this,
I already have a few SVG files that I put in my assets, lemme do a quick check. okay they r safe!

![Alt text](/assets/images/cat_loading.jpg)

#### File-Based Attacks
Not only images, there are other files that can be used to attack.

| File type | Attack method |
| --- | --- |
| **Executable (.exe)** | Directly runs malicious code in memory |
| **PDF** | Embeds scripts, objects, or malicious links |
| **Compressed files (.zip, .rar)** | Obfuscates malware inside hundreds of files |
| **Office documents (.docx, .xlsx)** | Malicious **macros** — gather data, phone home, execute payloads |
| **Browser extensions / add-ins** | Extension itself contains malware — installed voluntarily by the user |

#### Voice/Phone Vectors
- Voice phishing, calling to impersonate
- SPIT (Spam over Internet Telephony) to automate spam calls
- War Dialing to scan for phone numbers with direct dial-in access

I do see some friends almost getting scammed with the: <br>
Scammer: "eh hi [friend name], i changed my phone number, record it down eh <br>
Friend: "what, who are you?" <br>
Scammer: "aiya, how can you forget me? The one that wears glasses and a little fat one la" <br>
Friend: "Joseph? (random name i came up with)" <br>
Scammer: "Yea yea yea" <br>

But I find it so fun cuz I can be saying the most random stuff and the scammer has to
play along to earn my trust.

#### Removable Media (USB)
Woa its the movie moment where u plug it in and u start extracting the company secret files.
It is especially effective against air-gapped networks with no direct internet connection.

Some USB can even disguise as keyboard to automatically type commands when connected. (USB HID spoofing)
Attack relies on curiosity.

#### Vulnerable Software
There are multiple scenarios:

| Scenario | Risk |
| --- | --- |
| **Known vulnerability, unpatched** | Attacker exploits the gap between patch release and your deployment |
| **Unknown vulnerability (zero-day)** | Attacker finds it first — no patch exists yet |
| **Web-based / agentless apps** | Compromise the central server = infect all connecting clients simultaneously |
| **Unsupported software / OS** | No patches available — permanent vulnerability window |

Take note of old inventory, Old systems, avoid these with inventory management and isolation.

#### Network Infrastructure
There are network vulnerabilities too that we have to take note of such as:

| Vector | Risk |
| --- | --- |
| **Outdated wireless protocols** | WEP, WPA, WPA2 have known vulnerabilities — upgrade to WPA3 |
| **Rogue access points** | Unauthorised WAPs providing easy network entry |
| **Lack of 802.1X** | No port-based authentication = anyone can plug in and connect |
| **Bluetooth** | Used for reconnaissance or exploiting Bluetooth implementation weaknesses |


#### Open Service Ports
Ports are open for services but the more ports opened, the larger the attack surface. 
Misconfigurations can cause unauthorised access and we need to make use of firewalls well.

#### Default Credentials
Please change your password and stuff after receiving it for the first time. Many routers and switches 
are shipped with the default admin or share similar default.

#### Supply Chain
Attackers can attack from the source and just gain access by riding inside trusted weapon or 
through third party relationships.

---

![Alt text](/assets/images/fishing.jpg)

## More about Phishing
It is a social engineering with a touch of spoofing.

Check for its URL! Its content! Its format!

#### Phishing Variants
**Phishing** - email
**Smishing** - SMS/Text
**Vishing** - Voice/Phone
**Spam/Unsolicted** - Email/IM

#### Some Phishing techniques that they use
**Typosquatting**: registers a domain almost identical to a legitimate one, URL Hijacking

**Pretexting**: Attacker fabricates a convincing story to pull you into a scenario

**Spoofed Sender Addresses**: Email appears to come from a trusted organisation but address is fake 
or very close

**Urgency/Deadline Pressure**: Designed for short-circuit careful thinking, social engineering trigger

**Fake Login Page**: From clicking into phishing link leading to a near-identical copy of a real login
page, but there are slight differences. Credentials will be stolen!


![Alt text](/assets/images/impersonation.jpg)

## Impersonation
Attacker pretends to be a trusted person or organisation to get target comfortable to hand over
information or access.

#### Impersonation Techniques
1. Pretending to be colleague or help desk
2. Pretending to be Authority or senior staff
3. Use excessive technical jargon to distract
4. Spoofed Caller ID or email to appear to be trusted

#### Elicitation
Impersonation is often used to elicit (draw out) specific information. *Paired with a story.*

#### Identity Fraud
Attacker becomes victim by using stolen personal information for scenarios like:
- Credit card fraud
- Bank account fraud
- Loan fraud
- Tax fraud

#### How to protect yourself?
With common sense! JK, other than common sense there's also establishing verification procedures
in the organisation, performing independent verification and be sceptical about unsolicited contacts.

<br>

![Alt text](/assets/images/watering_hole.jpg)

## Watering Hole Attack
Attackers will attack a **third party website** that the target organiation is known to visit,
and then wait for target to come. This is to target a **weaker intermediary that the target trusts**.

**Broad Poisoning**: Attacker can choose to infect all visitors and will zoom into target when target 
falls prey too. 

**Targeted Poisoning**: Attackers can choose to only execute for specific IP addresses


> Real World Example: Polish Financial Supervision Authority in 2017
> Attackers compromised 3 financial regulator websites and used Targeted Poisoning on banks
{: .prompt-info}


#### Defending against Watering Hole Attacks
Defense-in-depth, we need multiple layers of defence (**layered defence**). Increasing the odds
of recognising and blocking malicious software.

## Other Social Engineering Attacks

#### Misinformation/disinformation
**Difference**: misinformation is unintentional while disinformation is deliberate.

However, both are social engineering attacks that weaponsises false information to
divide, confuse or manipulate people.

e.g. Influence Campaigns (political) through social media

![Alt text](/assets/images/misinformation_process.jpg)
A screenshot from Professor Messer's Youtube Video on Other Social Engineering Attacks.


#### Brand Impersonation
Attackers can create hundreds or thousands of fake websites using well-known brand names
to epxloit the trust that user has in those brands.

---

# Summary
There are so many different ways to attack and I think it is the first time I see a structured
ordered presentation of the different attack surfaces, very interestinggggg! And this is it for
my first intense Security+ content day so heres a sunrise picture signifing a start!


![Alt text](/assets/images/sunrise.jpeg)