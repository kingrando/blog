---
title: "AZ900 - Create an Azure Account"
date: 2020-09-09T19:00:00-05:00
draft: false
tags:
  - Azure Fundamentals
  - AZ900
categories:
  - Certifications
  - Microsoft
  - Cloud
---

## Understand Azure Billing

### Azure Subscriptions

When you create an account, an Azure subscription is created for you by default. This is a logical container that houses all of your Azure resources such as VMs. As you create more resources, you will assign those resources to a subscription.

You may also want to or need to create additional Azure subscriptions. This can be because of:

* **Environments**: You may want to separate testing from production or based on security requirements/policies.
* **Organizational structure**: You can limit teams to certain resources
* **Billing**: Track various costs across departments
* **Subscription Limits**: Some resources have hard limits within a subscription such as ExpressRoutes

Subscriptions can be organized into invoice sections. Each invoice section can contain multiple Azure subscriptions. The invoice section is then tied to a Billing profile which is then in turn tied to a Billing account.

Billing Account > Billing Profile > Invoice Section > Azure Subscription

## Azure Support Options

### Free Support Options

* 24/7 access to online documentation, community support, and feature demos on YouTube
* Billing and subscription management support
* Azure QuickStart Center: Increase your knowledge of Azure
* Azure Service Health: Insights on issues related to your services
* Azure Advisor: Recommendations to optimize cost and performance

### Support Plans

| | Developer | Standard | Professional Direct |
|---|---|---|---|
| Best for | Non-critical workloads | Production workloads | Business-critical workloads |
| Reactive technical support | 1 business day response | 1-hour response for critical cases | 1-hour response + priority tracking of critical cases |
| Proactive technical support | Not applicable | Not applicable | Access to a pool of technical experts |

### Community Support

| Channel | Description |
| --- | --- |
| **Azure Knowledge Center** | The Azure Knowledge Center is a searchable database that contains answers to common support questions. |
| **Microsoft Tech Community** | Get support by reading responses to Azure technical questions from Microsoft's developers and testers. |
| **Microsoft Q&A** | Find answers to your technical questions about selected Azure products. |
| **Stack Overflow** | You can review answers to questions from the development community. |
| **Server Fault** | Review community responses to questions about System and Network Administration in Azure. |
| **Azure Feedback Forums** | Read ideas and suggestions for improving Azure made by Azure users. |
| **Twitter** | Tweet @AzureSupport to get answers and support from the official Microsoft Azure Twitter channel. |

## References

* [Create an Azure Account](https://docs.microsoft.com/en-us/learn/modules/create-an-azure-account/)
