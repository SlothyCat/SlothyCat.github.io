---
title: "Change Management"
date: 2026-05-04 14:46:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/change_management.jpg
  alt: Change Management
---

# About Change Management
It refers to the **formal process for controlling modifications** to systems, applications, and infrastructure in an organisation.
Without it, uncoordinated changes will cause outages, inconsistencies and security gaps. We need to have a standard procedure to follow
to avoid negative consequences.


> Negative Consequences include: breaking other systems, unclear of change, no way to undo, security patch not applied
{: .prompt-tip}

## Change Approval Process
1. Submit Form
2. Document Reason
3. Define scope of change
4. Schedule for change
5. Identify impact
6. Risk analysis
7. Board decision to approve ot deny
8. Implement
9. User verification that things work


**Owners**: Initiates change request, stays informed, verify after change but typically not the one
implementing
**Stakeholders**: Anyone impacted, should be identified and consulted before approval and decides schedule
**Change Control Board**: Review change submissions, analyse risk and decide if approve or deny


## Risk Analysis:
There are risks associated with change and we need to review if it is better for us to make the change or not.

### Risk from making the change
- Does not actually fix it
- Installing the patch breask something else
- OS failure after update
- Data corruption

### Risk from NOT making the change
- Security Vulnerability remains exploitable
- Application becomes unavailable
- Dependent services stop working

> We need to weigh both sides to decide
{: .prompt-tip}


## Sandbox Testing
We can test in a sandbox environment before making changes in production, test before deployment.
Confirm the backout plan here to make sure that there is a plan if things go wrong, dont wait until failure
in production!

> Sandbox Environment: No connection to real world or production, is a technological safe space
{: .prompt-info}

### Backout Plan (Rollback)
A way to revert your changes can be 1 step, multi step procedure or even have to restore to full backup. 

**Always take a full backup before making any changes, adds a layer of recovery on top of Backout Plan**


### Scheduling Considerations
Implement the changes on off-hours or times when there is minimal user impact. For 24/7 cases,
find the lowest-traffic window possible

> Consider retail networks during holiday season, we should avoid busy seasons when making changes


## Standard Operating Procedure
Change Management is critical and the process must be well documented. The Change Management
process itself, should be updated frequently too (a living document).


# Technical Change Management
It is **not a simple upgrade** when there are many different moving parts that will be affected. 
Change Management is the `why` and Technical Change Management is the `how`.

## Scope Constraints
As we recall in the Change Management procedure, this is declared. Technicians will follow the scope
and will not make unrelated changes. If there is a need to expand scope, they will have to follow
the formal procedure of expanding the scope.

## Downtime Management by technicians
Other than doing at low traffic periods, technicians can also have primary and secondary systems 
that can be switched around automatically. This can also be used for Rollback.

## More about technical changes
Restarts are normal for updates, there could be a OS reboot, service reboot or app reboot to see the changes.
Legacy Applications are very old and no one is there to maintain them, so before we making changes to them,
we need to make sure we document down clearly how the application is downloaded, used, configured and supported.
It is hard-ish to make sense of it but it is possible if we document it. Some changes are dependent on others
so we need to make sure that everything is updated sequentially to see the impact.

Always have good documentation on what are the impacts of the changes and also do proper version control so that
the change is not a big magical step.

# Summary
Changes in small projects can be simple and there is not much of a need to go through a thorough process but in
big organisations, we have to follow a procedure and make sure that the changes are clear and documentations done.

![Alt text](/assets/images/big_buddha.jpeg)
Not related at all but lets just look at a picture I took when I was in Kamakura!