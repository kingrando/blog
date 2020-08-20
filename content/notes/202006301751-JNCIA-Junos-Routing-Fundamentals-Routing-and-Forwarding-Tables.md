---
title: "JNCIA Junos | Routing Fundamentals: Routing and Forwarding Tables"
date: 2020-06-30T17:51:36-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Routing Table

As a router obtains information from various sources, it stores that information in the Routing Table. This information can be learned dynamically through protocols or through manual entry.

The routing table is used to determine the best active route for each destination.

On Juniper devices there are multiple routing tables:

  1. `inet.0`: IPv4 unicast routes
  2. `inet.1`: Multicast forwarding cache
  3. `inet.2`: Used by Multicast BGP routes to perform RPF checks.
  4. `inet.3`: MPLS path info
  5. `inet.4`: Multicast Source Discovery Protocol (MSDP) route entries
  6. `inet.6.0`: IPv6 unicast routes
  7. `mpls.0`: MPLS next hops

When looking at a routing table, an `*` denotes an active route.

To view the routing table use: `show route`

```bash
kameron@RE2> show route

inet.0: 16 destinations, 16 routes (16 active, 0 holddown, 0 hidden)
+ = Active Route, - = Last Active, * = Both

0.0.0.0/0          *[Access-internal/12] 6w2d 20:43:09, metric 0
                    > to 192.168.30.1 via fxp0.0
2.2.2.2/32         *[Direct/0] 6w3d 20:49:02
                    > via lo0.0
3.3.3.3/32         *[OSPF/10] 03:55:05, metric 3
                    > to 10.0.3.2 via ge-0/0/1.0
```

## Forwarding Table

To enable devices to make faster decisions, a subset of the routing table is stored in the Forwarding Table. This table includes the destination prefixes and the outgoing interface used for that prefix.

To view the forwarding table use: `show route forwarding-table`

An ICMP destination unreachable message is sent by the router if an incoming packet matches the default forwarding entry.

Common Route Types Associated with Forwarding Entries:

* `dest`: Remote addresses reachable through an interface
* `intf`: Routes installed as a result of configuring an interface
* `perm`: Routes installed by the kernel when the routing table initializes
* `user`: Routes installed by the routing protocol process or as a result of the configuration

Common Next-Hop Types Associated with Forwarding Entries

* `bcast`: Broadcast
* `dscd`: Discard silently without sending an ICMP unreachable message
* `hold`: Next hop is waiting to be resolved into a unicast or multicast type
* `locl`: The local address on an interface
* `mcst`: Wire multicast next hop (limited to the LAN)
* `mdsc`: Multicast discard
* `recv`: Receive
* `rjct`: Discard and send an ICMP unreachable message
* `ucast`: Unicast
* `ulst`: A list of unicast next hops used when you configure load balancing

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
