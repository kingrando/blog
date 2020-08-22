---
title: "JNCIA Junos | Routing Fundamentals: Routing Instances"
date: 2020-06-30T18:12:36-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Routing Instance

A routing instance is defined as a group of routing tables, interfaces, and protocol parameters which is then used to control what information is in that routing table.

**Note:** There can only be one instance of each protocol per routing table.

By default, a unicast routing instances called `master` is created and includes the `inet.0` routing instance.

User-defined routing instances can be created at `[edit routing-instances]` hierarchy.

There are 12 types of Routing Instances that can be configured:

* Ethernet VPN (EVPN)
* Forwarding
* Internet Multicast over MPLS
* Layer 2 Backhaul VPN
* Layer2-control
* Layer2 VPN
* MPLS forwarding
* Nonforwarding
* Virtual router (This is the VRF)
* Virtual switch
* VPLS
* VRF

## Configuration

* Create a routing instance

  ```bash
  # Command
  set routing-instances <instance-name>
  # Example
  set routing-instances Instance-Example
  ```

* Configure the routing instance type

  ```bash
  # Command
  set routing-instances <instance-name> instance-type <instance-type>
  # Example
  set routing-instances Instance-Example instance-type virtual-router
  ```

* Assign interfaces to the routing instance

  ```bash
  # Command
  set routing-instances <instance-name> interface <interface-name>
  # Example
  set routing-instances Instance-Example interface ge-0/0/0 unit 0
  ```

## Example

* Create an additional OSPF Routing Instance

  ```bash
  # Create routing instance
  set routing-instances Network_10 instance-type virtual-router

  # Assign interfaces to the routing instance
  set routing-instances Network_10 interface ge-0/0/0.10
  set routing-instances Network_10 interface lo0.10

  #Setup the OSPF area
  set routing-instances Network_10 protocols ospf area 0.0.0.0 interface ge-0/0/0.10
  set routing-instances Network_10 protocols ospf area 0.0.0.0 interface lo0.10
  ```

## Verification

* Display the routing table

  ```bash
  kameron@RE3> show route

  Net_10.inet.0: 7 destinations, 7 routes (7 active, 0 holddown, 0 hidden)
  + = Active Route, - = Last Active, * = Both

  10.0.10.0/30       *[OSPF/10] 00:00:16, metric 2
                      > to 10.0.12.1 via ge-0/0/0.10
  10.0.12.0/30       *[Direct/0] 00:00:33
                      > via ge-0/0/0.10
  10.0.12.2/32       *[Local/0] 00:00:33
                        Local via ge-0/0/0.10
  11.11.11.11/32     *[OSPF/10] 00:00:16, metric 1
                      > to 10.0.12.1 via ge-0/0/0.10
  12.12.12.12/32     *[OSPF/10] 00:00:16, metric 2
                      > to 10.0.12.1 via ge-0/0/0.10
  13.13.13.13/32     *[Direct/0] 00:00:33
                      > via lo0.10
  224.0.0.5/32       *[OSPF/10] 00:00:34, metric 1
                        MultiRecv
  ```

* Display the routing instances

  ```bash
  kameron@RE3> show route instance
  Instance             Type
          Primary RIB                                     Active/holddown/hidden
  master               forwarding
          inet.0                                          17/0/0
          inet6.0                                         1/0/0

  Net_10               virtual-router
          Net_10.inet.0                                   7/0/0
          Net_10.inet6.0                                  1/0/0
  ```

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
* [Routing Instances Overview](https://www.juniper.net/documentation/en_US/junos/topics/concept/routing-instances-overview.html)
