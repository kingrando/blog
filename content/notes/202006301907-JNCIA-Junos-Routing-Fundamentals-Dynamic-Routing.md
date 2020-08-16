---
title: "JNCIA Junos | Routing Fundamentals: Dynamic Routing"
date: 2020-06-30T19:07:24-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Dynamic Routing Protocols
Dynamic Routing Protocols benefits:

  * *Lower administrative overhead* since routes are learned automatically instead of through manual entry.
  * *Increases network availability* because traffic can be rerouted automatically in the event of an outage.
  * *Greater network scalability* because dynamically learning routes allows for easier growth and deployment of new routers.

There are two primary classifications of dynamic routing protocols:

  1. *Interior Gateway Protocols (IGPs)* which operation within a single autonomous system (a network managed by a single entity). RIP, IS-IS, and OSPF are examples of IGPs.
  2. *Exterior Gateway Protocols (EGPs)* which operate among different autonomous systems. BPG is the only EGP in use today.

## Configure OSPF
  
  * Create OSPF area:
    * `set ospf area 0`
  * Assign interfaces to OSPF area:
    * `set ospf area 0 interface <interface_name>`

## Verify OSPF

  * Show overview of OSPF information:
    * `show ospf overview`
  * Show OSPF routing table:
    * `show ospf route`
  * Show OSPF neighbor status information:
    * `show ospf neighbor`
  * Show OSPF interface status information:
    * `show ospf interface`
  * Show OSPF link-state database:
    * `show ospf database`

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)

