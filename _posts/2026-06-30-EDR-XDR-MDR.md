---
title: "EDR, XDR and MDR"
date: 2026-06-30 21:30:00 +0800
categories: [Cybersecurity, Recap]
tags: [Cybersecurity, Recap]
image:
    path: assets/images/warrior.svg
    alt: Warrior Protecting Your Device and Network
---

# Security Concept Clarification: EDR, XDR and MDR
A sudden thought came to my mind while I was washing the dishes: what is the difference between EDR, XDR and MDR again? I remember studying it when I was preparing for the Security+ Examination, but I seem to have forgotten what they actually do, so it is a good time to have a quick recap!

I have made reference to [this post](https://www.sysdig.com/learn-cloud-native/edr-vs-xdr-siem-vs-mdr-vs-soar) on `Sysdig` while coming up with this post!

### EDR - Endpoint Detection and Response
As the name suggests, it works in the endpoint environment, and it is a security tool that detects, investigates and responds to threats.

We require endpoint security tools as another layer of defence if the threat manages to bypass firewalls or antivirus software. By being able to monitor behaviours and processes, they are able to detect and respond to malicious behaviours.


### XDR - Extended Detection and Response
XDR is a PRO version of EDR since it can now collect more data to uncover more sophisticated threats. The sources of data now include:
1. Cloud
2. Networks
3. Email
and others.

XDR tooling collects raw telemetry data and then integrate them to improve threat visibility. This was originally developed to help IT professionals to draw connections faster when flooded with more security feeds. This was not possible with the original EDR!


### MDR - Managed Detection and Response
MDR is a service offered by a managed security service provider (MSSP) or security tooling vendor. It is a combination of technology, processes and people that come together to detect and respond to cyber threats.

The MDR tools and services are meant to be continuous, allowing organisations that do not have a specialised team to have a comparable coverage while being cost-effective.

>Acronis has its MDR!
{: .prompt-info}


### Quick Comparison:
`EDR` - endpoint
`XDR` - endpoint, but with more source vectors
`MDR` - a service or tool that helps detect and respond

Hopefully that clears things up! And time for a case study!


### Case Study: Muji halts online sales after ransomware hits delivery supplier Askul

I had an interview with Acronis, but due to a time conflict, I was not able to continue with the interview process. However, I decided to ask **Mr Oleg**, my interviewer, for any advice that can prepare me for a role in **TRU**, and he said I could try to read up on some reports that TRU posts, so here I am!

The link for this post is [here](https://www.acronis.com/en/tru/posts/msp-cybersecurity-news-digest-october-21-2025/)

Okay, so basically, there was a **ransomware** attacking the supply chain, and it had a ripple effect on integrated payment and inventory databases. The **immediate actions recommended** were to isolate impacted networks, scan for ransomware, restore from offline backups and audit 3rd party security posts.

This was very similar to the steps that I have learned in Security+ as well, so yay!

The `Acronis Cyber Protect's Active Protection` was able to **block the encryption attempts by the ransomware**, while the `EDR/XDR` detected an **anomalous file access**.

The `Active Protection` actually has an AI behavioural engine that monitors processes on endpoints to identify and block ransomware and zero-day threats in real-time.

It managed to identify the ransomware and reverted using cache to instantly revert affected files, which was kinda cool.

This layer of security managed to help prevent that attack, as the ransomware did manage to get through the other layers of security to get to the endpoint and execute the process. This goes to show the importance of security in depth, and we should always try to cover as many bases as possible!

# Summary
Today was a really quick review on the concept, but it was engaging and fun to have a small read after work! Maybe more of this series if my ADHD brain bounces another concept out while washing dishes again!

![alt](/assets/images/busan_nightview.jpeg)
Busan night near the beach.