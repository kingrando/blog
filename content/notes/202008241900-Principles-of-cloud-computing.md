---
title: "AZ900 - Principles of Cloud Computing"
date: 2020-08-24T19:00:00-05:00
draft: false
tags:
  - Azure Fundamentals
  - AZ900
categories:
  - Certifications
  - Microsoft
  - Cloud
---
## Services Offered

There are 4 general categories of services that cloud providers typically offer:

* **Compute Power**: Services used for computation and processing tasks
  * **Virtual Machines**: You receive a portion of resources and install your own OS and software
  * **Containers**: These are an isolated environment that is used to run applications in a consistent manner. Most popular platform is Docker
  * **Serverless computing**: Allows you to run application code without server infrastructure
* **Storage**: Services for files and databases
  * Store a file
  * Create relationships using a database
* **Networking**: Services for connecting your network to the cloud provider
* **Analytics**: Services used to gather and visualize data

## Benefits of Cloud Computing

* **Cost-Effective**: Provides a pay-as-you-go model based on your consumption. This allows you to only pay for what you need, when you need it
* **Scalable**: Provides the ability to scale up (vertical scaling), which is adding more resources to your existing server, or the ability to scale out (horizontal scaling), which is adding more servers
* **Elastic**: Automatically add and remove resources based on demand
* **Current**: You do not have to worry about keeping your infrastructure patched and up-to-date
* **Reliable**: Offers built-in backup, replication, and disaster recovery
* **Global**: Regional data centers that serve you and your customers from the closet data center
* **Secure**: Physical and digital security of your cloud infrastructure

## Compliance Offerings

* **Criminal Justice Information Services (CJIS)**: Required to adhere to the CJIS Security Policy if a state or local agency wants to access the FBIs CJIS database. Azure is the only major cloud provider that is contractually committed to enforcing this.
* **Cloud Security Alliance (CSA) STAR Certification**: A cloud organization has achieved ISO/IEC 27001 certification and met specific criteria within the Cloud Controls Matrix (CCM).
* **General Data Protection Regulation (GDPR)**: European privacy law.
* **EU Model Clauses**: Azure data transfers meet privacy protections for international data transfer.
* **Health Insurance Portability and Accountability Act (HIPAA)**: Azure adheres to specific security and privacy provisions put forth in the Health Information Technology for Economic and Clinical Health (HITECH) Act.
* **International Organization for Standardization (ISO) and the International Electrotechnical Commission (IEC) 27018**: Covers processing of personal information by a cloud provider.
* **Multi-Tier Cloud Security (MTCS) Singapore**: Received the MTCS 584:2013 certification across IaaS, PaaS, and SaaS.
* **Service Organization Controls (SOC) 1, 2, and 3**: Independent third-party security audits.
* **National Institute of Standards and Technology (NIST) Cybersecurity Framework (CSF)**: Voluntary framework that outlines security best practices.
* **UK Government G-Cloud**: Certification used obtained by cloud providers that are used by the UK government.

## Economies of Scale

One of the cost benefits of using a cloud provider. A cloud provider can acquire things cheaper and then pass on those savings to the customer. For example, they can buy 100 servers at $1000s in a bulk purchase while it may cost you $10000 for one server.

## Capital expenditure (CapEx) versus operational expenditure (OpEx)

Companies have two investment strategies at their disposal.

**Capital expenditure** which is spending money up front for something and **Operational expenditure** which is spending money for products or services over time.

CapEx usually has the following costs:

* Server
* Storage
* Network
* Backup and archive
* Organization continuity & disaster recovery
* Datacenter infrastructure
* Technical personnel

A benefit of CapEx is that the costs can usually be planned for and budgeted properly. On the other hand, it can be hard to predict demand and growth which can outpace what you have budgeted and planned for.

OpEx is usually has the following costs:

* Leasing software and customized features
* Scaling charges based on usage/demand
* Billing at the user or organization level

OpEx can allow you to try products and services without investing in the hardware upfront. It also allows you to be *agile* and pay for the services for a high demand month and then back down once the demand is over.

## Cloud Deployment Models

### Public Cloud

Public clouds are the most common type (Azure, Google Cloud, AWS). When using a public cloud provider, you have no physical hardware, instead everything runs on your cloud providers infrastructure.

#### Advantages

* High scalability/agility
* Pay-as-you-go pricing
* Not responsible for maintenance, updates, or hardware
* Minimal technical knowledge required to setup and use

#### Disadvantages

* May not meet specific security requirements
* May not meet various standards or policies required by government, industry, or legal agencies
* Since you do not own the hardware, you cannot manage them how you would like
* May be hard to maintain legacy applications

### Private Cloud

A private cloud is hosted in your datacenter and emulates a cloud provider except you own and support the infrastructure.

#### Advantages

* Ensure the ability to support legacy applications
* Control and responsibility of security
* Can meet strict security guidelines

#### Disadvantages

* CapEx costs to build out a datacenter
* Difficult to remain agile and scale to meet demand
* IT support staff to build and maintain

### Hybrid Cloud

A hybrid cloud enables you to use the type of cloud, either public or private, that best fits your application or service scenario. For example, running a website in a public cloud and your CRM platform in a private cloud.

#### Advantages

* Can use out-of-date hardware and software to keep legacy systems running
* Flexibility to run in the cloud or on-premise
* Use economies of scale for where it matters
* Use own equipment to meet compliance and standards

#### Disadvantages

* Can be expensive because of upfront CapEx
* Can be more complicated to setup and get going

## Types of Cloud Services

### Infrastructure as a Service (IaaS)

IaaS is essentially renting hardware from a cloud provider. You have control over the amount of resources you use for CPU, storage, networking, etc...

IaaS is commonly used to:

* Migrate workloads
* Test and development environments
* Storage, backup, and recovery

There is no upfront costs associated with IaaS. Instead users pay for what they use.

The user is responsible for obtaining, purchasing, and installing their own OS and applications. The cloud provider is responsible for ensuring the underlying infrastructure is available for the user.

### Platform as a Service (PaaS)

PaaS is used for building, testing, and deploying software applications.

PaaS is commonly used for:

* Development framework
* Analytics or business intelligence

There is no upfront costs associated with PaaS. Instead users pay for what they use.

The user is responsible for the development of their own applications but the cloud provider is responsible for everything else.

### Software as a Service (SaaS)

SaaS is a cloud hosted software application such as SalesForce or Microsoft Office 365.

There are no upfront costs associated with SaaS. Instead users usually pay a monthly or annual subscription.

The user has no responsibility for the maintenance or management of the software.

## References

* [Cloud Concepts – Principles of cloud computing](https://docs.microsoft.com/en-us/learn/modules/principles-cloud-computing/)
