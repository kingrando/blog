---
title: "JNCIA Junos | Routing Policy and Firewall Filters: Routing Policy"
date: 2020-06-30T19:21:01-05:00
draft: false
type: "zettel"
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id: 
  - "5"
  - "6"
---
## Routing Policy
Routing policies are used to control the flow of information regarding the routing protocols to and from the routing and forwarding tables. This enables you to control what routes you want your devices to store. 

### Why use Routing Policies?
A routing policy can be used to help with one of the following scenarios:

  * You don't want to learn import all routes that a router sees.
  * You don't want to export all routes from a router.
  * You want to redistribute routes between routing protocols.
  * You want to manipulate some attribute about the route such as it's AS path.
  * You want to change the default BGP route flap-dampening parameters.
  * Perform per-packet load-balancing
  * Enable CoS

### Router Flows
Routing policies affect the following three traffic flows:

  1. *Routing information*: Information being shared between the routing protocols.
  2. *Data packets*: Transit traffic through the router.
  3. *Local packets*: Traffic sent by the router.

### Types of Routing Policies
**Import Policies** control how routes are added to the routing instance. Junos applies these policies **BEFORE** they are added to the routing instance. 

**Export Policies** control how routes are sent from the routing table. (**Note**: Inactive routes cannot be exported)

### Default Routing Policy
The following outlines the default routing policies for 4 major dynamic routing protocols.

  * BGP
    * **Import**: Accept all BGP routes and import into inet.0
    * **Export**: Accept all active BGP routes
    * Configurable at the protocol, group, and neighbor levels
  * OSPF
    * **Import**: Accept all OSPF routes and import into inet.0
    * **Export**: Reject everything (protocol floods by default)
  * IS-IS
    * **Import**: Accept all IS-IS routes and import into inet.0
    * **Export**: Reject everything (protocol floods by default)
  * RIP
    * **Import**: Accept all RIP routes from explicitly configured neighbors and import into inet.0
    * **Export**: Reject everything

### Building Blocks
A routing policy is made up of 4 building blocks:

  * **Policy Name**: A user-defined name that is referenced within the configuration.
  * **Term(s)**: User defined rule names that are matched based on criteria.
  * **From statements**: Determine the match conditions.
  * **Then statements**: The action to take if the conditions are matched.




## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
  * [Policy Framework Overview](https://www.juniper.net/documentation/en_US/junos/topics/concept/policy-routing-overview.html)

