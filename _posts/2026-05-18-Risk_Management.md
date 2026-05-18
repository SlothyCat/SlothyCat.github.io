---
title: "5.2 Risk Management"
date: 2026-05-18 11:15:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/risk_management.jpg
  alt: Risk Management
---

# Introduction to Risk Management

## Risk Management
The purpose is to identify and manage risks before they escalate. We need to qualify threats from both inside and outside the organisation and this becomes more critical as the company grows larger.

#### Types of Risk Assessments
**One-Time**: performed for a specific project or circumstance (company acquisition, new equipment) <br>


**Ad-Hoc**: performed for one specific purpose only, triggered by a specific concern or event. Focusing on only one risk type. The committee will be formed and disbanded, and is unlikely to be repeated for the same specific threat.<br>


**Recurring**: performed on a standard schedule

There can be both internal and mandated assessments, where internal is carried out by the organisation's own security/risk team, while mandated is usually external regulations or standards.

> So internal audit and external audit kinda thing, similar to what I am experiencing now in my internship!
{: .prompt-info}

## Risk Analysis
We will also have to analyse the risks associated with using qualitative and quantitative methods. This helps us with prioritisation.

#### Qualitative Risk Assessment
Evaluates risk factors using broad descriptive terms rather than specific numbers.
- Low, Medium, High
- Factors: impact, annualised rate of occurrence, cost of controls, overall risk
This is good for prioritising where to focus resources on.

#### Quantitative Risk Assessment
Calculates the specific financial values for risk
- Annualised Rate of Occurrence (ARO)
- Asset Value (AV)
- Exposure Factor (EF)
- Single Loss Expectancy (SLE): SLE = AV x EF
- Annualised Loss Expectancy (ALE): ALE = ARO x SLE

#### Risk Impact Categories

|Category|Priority|
|---|---|
|**Life**|Highest — people cannot be replaced|
|**Property**|Buildings and physical resources|
|**Safety**|Impact on individuals and the company|
|**Financial**|Calculated through quantitative analysis|

#### Likelihood vs Probability
**Likelihood** belongs to **qualitative** while **probability** belongs to **quantitative**. However, a probability value can be converted into a likelihood category.

#### Risk Appetite and Risk Tolerance

|Term|Definition|
|---|---|
|**Risk appetite**|The level of risk an organisation is willing to accept — a target or goal|
|**Risk tolerance**|A wider acceptable variance around the appetite — how far above appetite before action is taken|

Risk Appetite posture: Conservative, Neutral, Expansionary

#### Risk Register
A **documented list of all risks associated with a project or organisation**. Field could include:
1. Key Risk Indicator - what risk it is
2. Owner - who is responsible for managing that risk
3. Risk Threshold - how much risk is acceptable until action needs to be taken
4. Cost vs Impact - balance between cost to resolve risk and cost if risk is realised

## Risk Management Strategies
Organisations have different strategies to manage risk after identifying it.

|Strategy|Definition|Example|
|---|---|---|
|**Transfer**|Move the risk to a third party|Purchase cybersecurity insurance|
|**Accept**|Acknowledge the risk and decide to live with it|Most common course of action|
|**Avoid**|Completely remove the risk from the organisation|Stop using a risky technology entirely|
|**Mitigate**|Reduce the impact or likelihood of the risk|Deploy a next-generation firewall to reduce internet-based risk|

#### Accept - Exemption vs Exception
**Exemption**: A policy cannot be followed for a specific device or situation, and the management approves to **permanently** bypass the policy for that use case

> Manufacturer does not support OS patching. Keep it off the network but still make use of the equipment
{: .prompt-info}

**Exception**: A policy cannot be followed **temporarily** due to a conflict. A time-limited deviation is approved.

> Normally, the patch should be out in 3 days, but due to time and complexity, it has been allowed more than 3 days for the patch
{: .prompt-info}

#### Risk Reporting
The risk report is a **continuously updated document** tracking all the organisational risks, containing:
1. List of all tracked risks
2. Critical Risks
3. Emerging Risks
4. Handling options
This is normally used by upper management for **business decisions**.

## Business Impact Analysis
There are metrics to measure how well we recover from our downtimes. We have seen some of these before but it is time to really understand them.

#### RTO - Recovery Time Objective
How long before we are up and running? This is the **time frame from outage to full operational status**. This is defined by organisations, and managers normally want this number immediately when an outage occurs.

#### RPO - Recovery Point Objective
How far back in time must our data go to consider ourselves operational? We need to define a minimum data state that we need to resume operations. This is **usually a business requirement** and not a technical one.

> For example, an organisation might have the last 12 months of customer data before they consider themselves operational. Then the RPO is 12 months. The backups must contain at least that much data to be considered operational.
{: .prompt-tip}

#### MTTR - Mean Time To Repair
The **average time to fix a problem and restore the service**.
- Time to diagnose the problem
- Time to obtain a replacement
- Time to install the replacement
- Time to configure and restore the system

We can restore the MTTR if we have a contract with a third party within a guaranteed window. We can also keep spares on site and spend more money on standby equipment.

#### MTBF - Mean Time Between Failures
This is the **estimated time a system will run before the next failure.**
- This metric is used for planning
- Often provided by the manufacturer as a prediction
- Can also be calculated from historical data
	- Total Uptime / Number of Breakdowns


# Summary
This chapter feels much like the other chapter 5.1, we are moving onto more of how companies view security than how engineers view security. Cool insights and I believe everything introduced here will serve as a good foundational knowledge in the corporate world.

![alt text](/assets/images/sunset_kamakura.jpeg)
Sunset at Kamakura! There is a couple taking wedding picturesss! 