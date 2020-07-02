---
title: "JNCIA Junos | Routing Fundamentals: Routing Instances"
date: 2020-06-30T18:12:36-05:00
draft: false
type: "zettel"
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id: 
  - "5"
---
## Routing Instance
Routing instance is defined as a group of routing tables, interfaces, and protocol parameters. The routing instance is then used to control what information is in the routing table. 

**Note:** There can only be one instance of each protocol per routing table. 

By default a unicast routing instaces called `master` is created and includes the `inet.0` routing instance.

User-defined routing instaces can be created at `[edit routing-instances]` hierarchy:

  * Filter-based Forwarding (FPF)
    * `forwarding`: Used to implements a filter-based forwarding for common Access Layer applcations.
    * `no-forwarding`: Used to separate large networks into smaller administrative entities.
  * Layer 2 and Layer 3 VPN Services
    * `l2vpn`: Used in Layer 2 VPN implementations
    * `vpls`: Used for point-to-multipoint LAN implementations between a set of sites in a VPN
    * `vrf`: Used in Layer 3 VPN implentations
  * System Virtualization
    * `virtual-router`: Used for non-VPN-related applications, such as system virtualization

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
  * [Routing Instances Overview](https://www.juniper.net/documentation/en_US/junos/topics/concept/routing-instances-overview.html)