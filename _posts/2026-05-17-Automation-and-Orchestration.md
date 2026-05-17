---
title: "4.7 Automation and Orchestration"
date: 2026-05-17 10:35:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/automation.svg
  alt: Automation and Orchestration
---

# Introduction
I just finished a Python script to automate consolidating excel files and extracting the values I want and putting them together into a consolidated version with summaries and record entries in my internship on my first week. My personal feeling towards scripting is that most of the small tiny things that are repetitive and mundane are automated by interns who join the company as these are mostly independent of the work that the full-time employees do. Implementing it will help them to save time in the long run.

I feel like scripting is not as fun but still a useful thing to have.


## Benefits of Scripting & Automation

| Benefit | Detail |
| --- | --- |
| Speed | Runs at compute speed — no human typing delays or errors |
| Consistency | Same result every run — no typos, no missed steps |
| 24/7 operation | Runs without human presence — no phone calls in the middle of the night |
| Proactive identification | Scripts can identify problems before they occur and resolve them automatically |
| Security baseline enforcement | Scripts deploy patches, configs, firewall rules automatically |
| Scalability | Cloud infrastructure (servers + security devices) scales up/down via script |
| Reduced toil | Frees staff from boring repetitive tasks to focus on higher-value work |

---

## Automation Use Cases

| Use Case | How Automation Helps |
| --- | --- |
| **Patch deployment** | Script detects new patch in folder → deploys to all systems automatically |
| **Infrastructure config** | Default router/firewall configs deployed consistently at every new site |
| **Cloud scaling** | New servers + security devices provisioned together via script |
| **Onboarding** | Script creates account, assigns groups, sets home directory, grants email access |
| **Offboarding** | Script removes access and deactivates account on departure |
| **Guardrails** | Automated verification blocks dangerous commands (e.g. accidental mass-delete) |
| **Security group monitoring** | Alert fires if a user is added to the administrator group |
| **Help desk ticketing** | Email → ticket → assigned to correct team member automatically |
| **Service enable/disable** | Script activates a service for a defined window, then disables it |
| **API control** | Script communicates to device APIs — no manual console login needed |
| **Proactive monitoring** | Script detects low disk space → clears temp files before outage |
| **Escalation** | If script can't resolve a problem, automatically escalates to the on-call technician |

---

## Limitations & Risks

| Limitation | Detail |
| --- | --- |
| Complexity | Scripts interact with many systems — extensive testing required |
| Development cost | Someone must write, test, and maintain the script — time and money |
| Single point of failure | If the script breaks, all dependent systems may be affected |
| Technical debt | Scripts that mask root problems increase long-term maintenance burden |
| Ongoing maintenance | OS updates, language changes, API changes may break existing scripts |

> **Technical debt:** using automation to hide a deeper underlying problem rather than fixing it. A script resolving a symptom repeatedly instead of addressing the root cause increases technical debt over time.
{: .prompt-info}

# Summary
I see that there are the impact of having scripts more now, rather than the tiny tasks that I did for internship. There are important time savers and efficient methods of operating. I wonder if there is like a particular role for scripting lmao.

![alt text](/assets/images/chongqing_bear.jpeg)
Bearrr