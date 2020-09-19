---
title: "AZ900 - Core Cloud Services - Azure Architecture and Service Guarantees"
date: 2020-09-11T19:00:00-05:00
draft: false
tags:
  - Azure Fundamentals
  - AZ900
categories:
  - Certifications
  - Microsoft
  - Cloud
---
## Datacenters and Regions

A region is a geographic area that contains one more datacenters that are networked together. For example, South Central US, West Europe, Brazil South, and East Asia are all regions.

There are also a few special regions that are used for legal or compliance reasons including:

* **US DoD Central, US Gov Virginia**, US Gov Iowa: These are physically and logically isolated networks for government agencies and partners
* **China East and China North**: A unique partnership through Microsoft and 21Vianet, in which the datacenters are not managed by Microsoft

## Geographies

Geographies are Azure markets separated by geopolitical boundaries or country borders. They typically consist of two or more regions that preserve data residency and compliance boundaries.

The benefits include:

* A customer's applications are kept close together
* Data compliance, residency, resiliency, and sovereignty requirements are honored within that boundary
* Fault-tolerant in the event of complete region failures

There are 4 distinct geographies:

* Americas
* Europe
* Asia Pacific
* Middle East and Africa

## Availability Zones

Availability zones are physically separate datacenters within an Azure region. They are setup to be an *isolation boundary*, each having separate power, cooling, and networking. This ensures that if one zone goes down the others continue to work.

The following regions have at least three separate zones:

* Central US
* East US 2
* West US 2
* West Europe
* France Central
* North Europe
* Southeast Asia

Your apps can be replicated to other zones to improve availability and fault tolerance. However, this can cost additional resources.

The services that support Availability Zones fall into two categories:

* **Zonal services** - Pin the resource to a specific zone (ex: vms, disks, IP addresses)
* **Zone-redundant services** - Platform replicates automatically across zones (ex: Zone-redundant storage and SQL Database)

## Region Pairs

Each region is paired with another region at least 300 miles away. This reduces the likelihood that some event will affect both regions at once. If something happens to one region, the services automatically failover to another region.

Additional advantages include:

* If multiple regions are down, one region is prioritized so services are restored as quickly as possible
* Updates are rolled out one region at a time to minimize impact and downtime
* Data continues to reside in it's geography for tax and legal purposes

## Service-Level Agreements

Service-Level Agreements outline specific performance standards that Microsoft agrees to meet.

Performance targets are defined within an SLA that guarantee some uptime or connectivity rate for each Azure product or service.

The uptime and connectivity targets range from 2 nines (99%) to 5 nines (99.999%). These outline the amount of time that the service can be down during a week, month, or year.

If the uptime and connectivity guarantees are not met, Microsoft outlines a service credit percentage if the monthly uptime falls below a certain percentage. For example, if the service is < 99%, Microsoft will issue a 25% of the service credit.

## Compose SLAs Across Services

## Improve Your App Reliability

## Reference

* [Core Cloud Services - Azure architecture and service guarantees](https://docs.microsoft.com/en-us/learn/modules/explore-azure-infrastructure/)
