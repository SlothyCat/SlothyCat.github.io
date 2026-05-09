---
title: "3.4 Resiliency and Recovery"
date: 2026-05-09 11:53:00 +0800
categories: [Security+]
tags: [Security+]
image:
  path: assets/images/resiliency.jpg
  alt: Resiliency and Recovery
---

# Introduction to Resiliency and Recovery
What if things go wrong? What if our defences fail? What do we do next?

## Resiliency
It ensures that the systems stay available through failures. There are multiple strategies that we will be going through today to keep our systems resilient.

#### High Availability (HA)
Systems are always on and running; if one fails, the other takes over with no downtime! However, it requires extra hardware, more costly

#### Server Clustering
- Make use of multiple servers to act like one logical server.
- Users will only see it as a single resource
- Servers normally have the same OS and have shared storage
- Different from Load Balancing

| Property            | Server Clustering                   | Load Balancing                                  |
| ------------------- | ----------------------------------- | ----------------------------------------------- |
| Server awareness    | Each server knows all others        | Servers have no knowledge of each other         |
| Central coordinator | No single coordinator — distributed | Load balancer is the central control point      |
| OS requirement      | Usually identical OS                | Can use different OSes                          |
| Failure handling    | Cluster redistributes automatically | LB detects failure, removes node, redistributes |
| Scalability         | Add/remove nodes from cluster       | Add/remove servers from LB pool                 |

#### Recovery Sites
It is a place that is **pre-allocated to continue operations in the event of a disaster.** Data is synced in advance to make sure that they can continue to operate.

| Site Type     | What’s There                                               | Time to Activate | Cost    |
| ------------- | ---------------------------------------------------------- | ---------------- | ------- |
| **Hot site**  | Exact replica — all hardware, software, data in sync       | Near-immediate   | Highest |
| **Warm site** | Some equipment, some data — needs additional hardware/data | Hours to days    | Medium  |
| **Cold site** | Empty building with power and lighting only                | Days to weeks    | Lowest  |

We should make sure that the recovery site is far from the primary site so that the regional disaster will not compromise both at the same time.

#### Platform Diversity
Over-reliance on only 1 OS makes it vulnerable too, so we should **make use of different OS** to limit the impact of a single OS vulnerability.

#### Multi-Cloud Resilience
We can **make use of multiple cloud providers** so that if one fails, we can still make use of another provider.

#### Continuity of Operations Planning - COOP
This is when all technology fails; it documents down the non-technical fallback processes to keep things going.

> E.g. If POS system is down, then use paper receipts and manual transaction records
{: .prompt-info}



## Capacity Planning
It is hard to match the supply to demand properly. We want to avoid under-provision and over-provision and so we need to plan our capacity properly and make changes.

#### 3 Dimensions of Capacity Planning
**People**: Slowest dimension to adjust since it is hard to scale quickly
**Technology**: Must be chosen with scalability in mind from the start
**Infrastructure**: the difference between physical data centres and cloud

| Property           | Physical Data Center     | Cloud                           |
| ------------------ | ------------------------ | ------------------------------- |
| Provisioning speed | Days to weeks            | Minutes                         |
| Upfront cost       | High (hardware purchase) | Low (pay as you go)             |
| Scale up           | Buy more hardware        | Add instances via console       |
| Scale down         | Hardware sits idle       | Remove instances, stop paying   |
| reRight-sizing     | Difficult after purchase | Easy — adjust in near real time |


## Recovery Testing
Disaster recovery is **only useful if they have been tested**. Just like how we have fire drills! If we do not test them, we will **fail under pressure**, and we can **identify things that we should take note of** when we; actual experience a real disaster! However, we should keep it controlled so our **production systems are not affected**.

#### Tabletop exercise
A group walk-through around the table with just words.

**Pros**: Cheap, no risk to production and can have some value.
**Cons**: Do not test whether systems actually fail over correctly.

#### Failover Test
Actually triggers the failover to verify that the redundant system will automatically take over and in a transparent manner (users do not notice).

**Fallover infrastructure:** Dual ISP connections → redundant routers → redundant firewalls → multiple switches → servers with multiple links. If any component fails, a secondary path takes over automatically.

#### Simulation
We test security controls and user behaviour through simulated attacks. For example, the phishing emails you receive internally, password reset simulation and data exfiltration simulation.


## Backups
We have seen a lot of times already in this course that we should update our data, but let us learn more about backups!

#### Backup Planning Considerations
Before we start backing up, we need to know what and how are we backing up, we already know the why! 

|Variable|Options|
|---|---|
|Data volume|Megabytes to petabytes — affects media and schedule choice|
|Backup type|Full, incremental, differential, snapshot|
|Media|Local tape, HDD, cloud|
|Storage location|On-site, off-site, cloud|
|Software|Third-party or OS-built-in|
|Schedule|Hourly, daily, weekly, monthly|
|Encryption|Required for off-site and cloud; recommended everywhere|

#### On-Site vs Off-site Backup
On-Site would be like at the primary site while off-site can be the secondary site or a site that is geographically further away.

| Property         | On-Site                                      | Off-Site                            |
| ---------------- | -------------------------------------------- | ----------------------------------- |
| Speed of restore | Fast — data is local                         | Slower — must transfer over network |
| Cost             | Lower — no third-party storage fee           | Higher — storage facility cost      |
| Risk             | Vulnerable to same local disaster as primary | Survives local disaster             |
| Access           | Immediate                                    | Network-dependent                   |

The best practice is to make use of both of these backups

#### Backup Schedules
There are **multiple frequencies based on the use cases** and we can actually have multiple backup sets at different intervals.

#### Backup Security
Backups contain the same sensitive data as the ones in the production system, or sometimes even more. We should **encrypt all backups** so that even if the backup is stolen, it is unreadable. Always make sure that the **decryption keys are stored separately and securely**, since encrypted backups are useless without their key.

#### Snapshots
I remember this from operating from a VM. This is a **point-in-time copy of a virtual machine**. The snapshot can be captured manually or automatically.

#### Testing Backups
We should test the backups to make sure that they are usable:
1. **Actually restoring data** from backup
2. Confirming applications **can make use** of the restored data
3. Testing across **all the backup types and schedules**

#### Replication
Copying data to at least 1 remote location in near real time. The change adjusted to the sources is pushed to all replicated sites within seconds or minutes.

#### Journaling
This protects against database corruption caused by power loss mid-write.

**Procedure:**
1. Data is first written to journal on disk
2. Once confirmed in journal, it is written to the database
3. If power fails during journal write, the journal is lost and the database was untouched
4. If power fails during database write, restart and read the journal and complete the write
5. Once successfully written, the journal entry is deleted.



## Power Resiliency
Power is important in any IT and what if they fail us? We have 2 solutions

#### UPS - Uninterruptible Power Supply
It provides immediate battery-backed power when the main power fails. This is really meant for the short term, as we wont be storing so many batteries for the actual outages.

Its types:

|Type|How It Works|Best For|
|---|---|---|
|**Offline / Standby**|Runs on mains; internal switch flips to battery on failure|Basic protection, budget setups|
|**Line-interactive**|Can boost voltage during brownouts before switching to battery|Areas with frequent brownouts|
|**Online / Double-conversion**|Always runs from battery; mains continuously recharges it|Maximum protection; no switchover delay|


> However, Online/Double-conversion UPS is the cleanest power output that comes with the highest cost since systems always run on battery.
{: .prompt-info}


|Feature|Detail|
|---|---|
|Battery capacity|Determines how long systems can run during outage|
|Graceful shutdown|Signals connected systems to shut down safely before battery depletes|
|Outlet count|Number of devices the UPS can support|
|Surge/line suppression|Ethernet and phone line ports with additional suppression|


#### Generators
Ah. You again. It provides long term power as long as fuel is available. It can power an entire building or just specific circuits.

|Property|Detail|
|---|---|
|Duration|As long as fuel lasts — days or weeks if needed|
|Startup time|~1 minute ramp-up before providing stable power|
|Scale|Can power a full data center or partial building circuits|
|Indicator|Generator-powered outlets are typically labelled in facilities|

Since we have an issue with the start time, and UPS is short-term, normally we make use of UPS first and then the generator later.


# Summary
In this chapter, we are putting the security controls aside and seeing what we can do if things like a disaster hit us. How can we make sure we stay in production? Resilience and having backups all come with a price. literally, price. You will need more money!

![Alt text](/assets/images/busan_dinner.jpeg)
First dinner in Busan!