---
title: "4.6 Identity and Access Management"
date: 2026-05-17 09:35:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/iam.svg
  alt: Identity and Access Management
---

# Introduction to Identity and Access Management (IAM)
I have learned previously about identity security in the IdentityNow Professional course in Year 1, so hopefully this will be a refresher and not too heavy!

## IAM
This covers the full lifecycle of user access from provision to deprovision. We will also learn more about identity proofing, authentication, authorisation, ongoing monitoring and different protocols that enable centralised and delegated authentication.

#### The lifecycle
We will split the lifecycle of a user into onboarding, ongoing and offboarding. Ongoing would mean that we might have to modify permissions due to a role change or promotion.

We should adhere to least privilege, just enough permissions for the user's job.

#### Identity Proofing
We need to verify before assigning an account.

| Step        | Description                                                                                                                                                                             |
| ----------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Resolution  | Formal verification process at account creation                                                                                                                                         |
| Validation  | User provides something only they know (password, security questions)                                                                                                                   |
| Attestation | **Additional identity verification** — government ID (passport, driver's licence), in-person meeting, or automated credit report checks asking about previous addresses or owned assets |

#### Authentication Protocols
**LDAP - Lightweight Directory Access Protocol** <br>
This is the standardised protocol for accessing large network directories. Based on the **X.500 specifications** (ITU standard). attribute=value pairs, with the most specific attribute listed first. It will form an X.500 Directory Information Tree. Individual components are known as leaf objects. This is used by Active Directory and many other directory services.

The original version was actually DAP (Directory Access Protocol) running on the OSI protocol, but it has been updated to work more efficiently with other OS. 

**SSO - Single Sign-On** <br>
Provides credentials one time to have access to all available resources. However, there is a time limit. This is common in the Windows Environment via Active Directory

**SAML - Security Assertion Markup Language** <br>
Open standard for authentication and authorisation against a third-party database. There is the client, resource server and authorisation server. However, it is **not designed for mobile users**.

SAML authentication flow:

![alt text](/assets/images/saml_procedure.jpg)
This is a Screenshot from Professor Messer Youtube Video on IAM.

**OAuth** <br>
Authorisation Framework from Twitter, Google and many others. It is often paired with OpenID for authentication, as OAuth handles authorisation.

**Federation** <br>
Access a resource using credentials from a different organisation or service. Third parties can establish a federated network, and they must establish a trust relationship.


#### Interoperability
There are many different ways to communicate with an authentication server. The choice of which protocol to use depends on the company environment. Example: a new VPN concentrator supports LDAP — if you already have an Active Directory (LDAP) server, that's a perfect match.


## Access Controls
Authorisation is the process of ensuring only authorised rights are exercised. Access Control models define who sets permissions and how access decisions are made.

#### Least Privilege
We have heard this term a lot of times by now; it just means to set the rights and permissions to be the bare minimum to function.


#### Access Control Models

| /Model       | Who Sets Permissions               | Basis                                     | Security Level      |
| ------------ | ---------------------------------- | ----------------------------------------- | ------------------- |
| **MAC**      | Central administrator              | Labels (confidential, secret, top secret) | High                |
| **DAC**      | Data owner                         | Owner's discretion                        | Lower               |
| **RBAC**     | Administrator (via roles/groups)   | Job function / role                       | Medium-High         |
| **Rule-BAC** | Administrator (rules on objects)   | System-enforced rules                     | Medium-High         |
| **ABAC**     | Administrator (complex attributes) | Multiple combined criteria                | Highest flexibility |

**Attribute-Based Access Control (ABAC)** is the next-generation model, as it combines many different attributes instead of just labels, creating complex rule sets. Attributes include: IP address, Time of Day, desired action, relationship to data, device type and location, etc.

#### Time-Of-Day Restrictions
This can be applied across the different models as **an extra layer.** Of course, global companies must account for their time zones.

|Example|Restriction|
|---|---|
|Training room network|Inaccessible midnight–6am|
|Conference room access|Blocked after 8pm|
|R&D databases|Available 8am–6pm only|


## Multifactor Authentication
While I have learned about MFA, I have learned that there were 3 factors, but here we learn about an extra one, **somewhere you are**.

| Factor                 | Category   | Examples                                                               |
| ---------------------- | ---------- | ---------------------------------------------------------------------- |
| **Something you know** | Knowledge  | Password, PIN, unlock pattern                                          |
| **Something you have** | Possession | Smart card, USB security key, hardware token, software token, SMS code |
| **Something you are**  | Inherence  | Fingerprint, voiceprint, retina scan, facial recognition               |
| **Somewhere you are**  | Location   | GPS coordinates, IP address geolocation, cell tower triangulation      |

## Password Security
Password policies **enforce entropy and expiration**. Password managers store unique passwords per account. Passwordless authentication removes passwords, and JIT permissions are temporary admin access so that primary credentials are never exposed.

#### Password Policies

|Policy Element|Purpose|
|---|---|
|Complexity (upper/lower/numbers/symbols)|Increases entropy — harder to brute force|
|Minimum length (8+ characters)|Longer = exponentially harder to crack; requirements increasing as processing speeds improve|
|Passphrase / word combination|Length over complexity — easier to remember, harder to crack|
|Password expiration (30/60/90 days)|Limits exposure window if a password is compromised; timer starts when password is set|
|Password history|Prevents reuse of recent passwords|

#### Password Managers
- Stores all passwords in an **encrypted database**
- Access to the database requires additional authentication (master password + MFA tokens)
- Enables a **unique password per account** without memorisation
- Features: auto-generate strong random passwords, auto-fill forms, health check (compromised/weak passwords flagged)
- Available as: OS-built-in, third-party app, enterprise-wide solutions

Personally, I have not used Password Managers lol

#### Passwordless Authentication
Eliminates the password — solves reuse and memorisation problems.

|Example|Factor Used|
|---|---|
|Face recognition on phone|Something you are|
|Windows Hello PIN|Something you know (PIN, not password)|
|Hardware security key|Something you have|

This normally requires having an initial password set up!

#### Just-In-Time Permissions
Solves the problem of technicians needing **temporary admin access** without having permanent admin rights to their normal accounts.

The procedure:
1. Technician **requests** elevated access from a central **privileged access vault** (clearinghouse)
2. Vault evaluates the request against security policies previously configured
3. Vault generates **ephemeral (temporary) credentials** based on primary credentials — the primary credentials are never shown to anyone
4. Technician uses temporary credentials for the session
5. Credentials are **deleted after the session ends**

> Even if there is a breach, there are no persistent admin rights!
{: .prompt-tip}

# Summary
I think this included a lot more information than what I studied for Identity Security previously and even though I have noticed technologies like Passwordless Authentication, there was no exact term or concrete terminology to describe them. But with this chapter, I get to contextualise a lot of information that we already know in the real world.

![alt text](/assets/images/cat_wall.jpeg)
Some motivational cute wall paintings that I saw in Chong Qing.