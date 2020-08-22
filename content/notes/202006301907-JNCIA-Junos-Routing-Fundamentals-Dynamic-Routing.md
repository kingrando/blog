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

* *Lower administrative overhead* since routes are learned automatically instead of through manual entry
* *Increased network availability* because traffic can be rerouted automatically in the event of an outage
* *Greater network scalability* because dynamically learning routes allows for easier growth and deployment of new routers

There are two primary classifications of dynamic routing protocols:

  1. *Interior Gateway Protocols (IGPs)* which operation within a single autonomous system (a network managed by a single entity). RIP, IS-IS, and OSPF are examples of IGPs
  2. *Exterior Gateway Protocols (EGPs)* which operate among different autonomous systems. BPG is the only EGP in use today

## Configure OSPF
  
* Create OSPF area:

  ```bash
  # Command
  set protocols ospf area <area>
  # Example
  set protocols ospf area 0
  ```

* Assign interfaces to OSPF area:

  ```bash
  # Command
  set protocols ospf area <area> interface <interface_name>
  # Example
  set protocols ospf area 0 interface ge-0/0/0.0
  ```

## Verify OSPF

* Show overview of OSPF information:

  ```bash
  # Command
  show ospf overview
  # Output
  kameron@RE4> show ospf overview
  Instance: master
    Router ID: 4.4.4.4
    Route table index: 0
    LSA refresh time: 50 minutes
    Post Convergence Backup: Disabled
    Area: 0.0.0.0
      Stub type: Not Stub
      Authentication Type: None
      Area border routers: 0, AS boundary routers: 0
      Neighbors
        Up (in full state): 2
    Topology: default (ID 0)
      Prefix export count: 0
      Full SPF runs: 149
      SPF delay: 0.200000 sec, SPF holddown: 5 sec, SPF rapid runs: 3
      Backup SPF: Not Needed
  ```

* Show OSPF routing table:

  ```bash
  # Command
  show ospf route
  # Output
  kameron@RE4> show ospf route
  Topology default Route Table:

  Prefix             Path  Route      NH       Metric NextHop       Nexthop
                    Type  Type       Type            Interface     Address/LSP
  1.1.1.1            Intra Router     IP            2 ge-0/0/1.0    10.0.3.1
  2.2.2.2            Intra Router     IP            1 ge-0/0/1.0    10.0.3.1
  3.3.3.3            Intra Router     IP            2 ge-0/0/0.0    10.0.4.2
  5.5.5.5            Intra Router     IP            1 ge-0/0/0.0    10.0.4.2
  1.1.1.1/32         Intra Network    IP            2 ge-0/0/1.0    10.0.3.1
  2.2.2.2/32         Intra Network    IP            1 ge-0/0/1.0    10.0.3.1
  3.3.3.3/32         Intra Network    IP            2 ge-0/0/0.0    10.0.4.2
  4.4.4.4/32         Intra Network    IP            0 lo0.0
  5.5.5.5/32         Intra Network    IP            1 ge-0/0/0.0    10.0.4.2
  10.0.0.0/30        Intra Network    IP            3 ge-0/0/1.0    10.0.3.1
  10.0.1.0/30        Intra Network    IP            2 ge-0/0/1.0    10.0.3.1
  10.0.2.0/30        Intra Network    IP            3 ge-0/0/0.0    10.0.4.2
                                                      ge-0/0/1.0    10.0.3.1
  10.0.3.0/30        Intra Network    IP            1 ge-0/0/1.0
  10.0.4.0/30        Intra Network    IP            1 ge-0/0/0.0
  10.0.5.0/30        Intra Network    IP            2 ge-0/0/0.0    10.0.4.2
  ```

* Show OSPF neighbor status information:

  ```bash
  # Command
  show ospf neighbor
  # Output
  kameron@RE4> show ospf neighbor
  Address          Interface              State     ID               Pri  Dead
  10.0.4.2         ge-0/0/0.0             Full      5.5.5.5          128    36
  10.0.3.1         ge-0/0/1.0             Full      2.2.2.2          128    36
  ```

* Show OSPF interface status information:

  ```bash
  # Command
  show ospf interface
  # Output
  kameron@RE4> show ospf interface
  Interface           State   Area            DR ID           BDR ID          Nbrs
  ge-0/0/0.0          BDR     0.0.0.0         5.5.5.5         4.4.4.4            1
  ge-0/0/1.0          BDR     0.0.0.0         2.2.2.2         4.4.4.4            1
  lo0.0               DR      0.0.0.0         4.4.4.4         0.0.0.0            0
  ```

* Show OSPF link-state database:

  ```bash
  # Command
  show ospf database
  # Output
  kameron@RE4> show ospf database

      OSPF database, Area 0.0.0.0
  Type       ID               Adv Rtr           Seq      Age  Opt  Cksum  Len
  Router   1.1.1.1          1.1.1.1          0x8000062f   698  0x22 0xafd7  72
  Router   2.2.2.2          2.2.2.2          0x80000b50  1748  0x22 0xf970  60
  Router   3.3.3.3          3.3.3.3          0x80000b51   213  0x22 0xacaa  60
  Router  *4.4.4.4          4.4.4.4          0x80000b4a   748  0x22 0xc091  60
  Router   5.5.5.5          5.5.5.5          0x80000b4a    40  0x22 0x77c8  60
  Network  10.0.1.2         2.2.2.2          0x8000035e  2748  0x22 0x6259  32
  Network  10.0.2.1         1.1.1.1          0x8000035d   699  0x22 0xc3f8  32
  Network  10.0.3.1         2.2.2.2          0x80000015   748  0x22 0x8872  32
  Network  10.0.4.2         5.5.5.5          0x80000157  1042  0x22 0xf7a5  32
  Network  10.0.5.2         5.5.5.5          0x80000277  2040  0x22 0x7708  32
  ```

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
