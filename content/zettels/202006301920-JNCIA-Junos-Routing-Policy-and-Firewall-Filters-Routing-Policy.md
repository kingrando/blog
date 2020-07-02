---
title: "202006301920 JNCIA Junos Routing Policy and Firewall Filters Routing Policy"
date: 2020-06-30T16:21:01-05:00
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
Routing policies are used to control the flow of information to and from the routing instance. Policies can be configured to accept, reject, or modify specific attributes for routes.

### Types of Routing Policies
**Import Policies** control how routes are added to the routing instance. Junos applies these policies **BEFORE** they are added to the routing instance. 

**Export Policies** control how routes are sent from the routing table. (**Note**: Inactive routes cannot be exported)

### Default Routing Policy
The following outlines the default routing policies for 4 major dynamic routing procools.

  * BGP
    * **Import**: Accept all BGP rotues and import into inet.0
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

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)

