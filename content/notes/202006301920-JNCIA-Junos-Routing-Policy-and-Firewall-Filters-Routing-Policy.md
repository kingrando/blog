---
title: "JNCIA Junos | Routing Policy and Firewall Filters: Routing Policy"
date: 2020-06-30T19:21:01-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---

Routing policies are used to control the flow of information between the routing protocols and routing table and then from the routing table to the forwarding table. This enables you to control what routes you want your devices to store.

## Why use Routing Policies

A routing policy can be used to help with one of the following scenarios:

* You don't want to import all routes that a router sees
* You don't want to export all routes from a router
* You want to redistribute routes between routing protocols
* You want to manipulate some attribute about the route such as it's AS path
* Perform per-packet load-balancing
* Enable CoS

## Router Traffic Flows

Routing policies affect the following three traffic flows:

  1. *Routing information*: Information being shared between the routing protocols
  2. *Data packets*: Transit traffic through the router
  3. *Local packets*: Traffic sent by the router

## Routing Policy Types

**Import Policies** control how routes are added to the routing instance. Junos applies these policies **BEFORE** they are added to the routing instance.

**Export Policies** control how routes are sent from the routing table. (**Note**: Inactive routes cannot be exported)

## Default Routing Policy

The default policies are used when there is no explicitly applied policy.

The following outlines the default routing policies for 4 major dynamic routing protocols.

* **BGP**
  * **Import**: Accept all IPv4 and IPv6 BGP routes from configured neighbors and import into inet.0 and inet6.0 respectively.
    * Supported at Global, group, and peer
  * **Export**: Export all active BGP routes
    * Supported at Global, group, and peer
* **OSPF**
  * **Import**: Accept all OSPF routes and import into inet.0
    * Supported for external routes only
  * **Export**: Reject everything (protocol floods by default)
    * Supported at the global level
* **IS-IS**
  * **Import**: Accept all IS-IS routes and import into inet.0
    * Supported level was not mentioned
  * **Export**: Reject everything (protocol floods by default)
    * Supported at the global level
* **RIP**
  * **Import**: Accept all RIP routes from explicitly configured neighbors and import into inet.0
    * Supported at the global and peer levels
  * **Export**: Reject everything
    * Supported at the group level

When applying policies, it's important to remember that the most explicit policy is sent (Peer > Group > Global).

## Active and Inactive Routes

When a routing table has multiple routes for a destination prefix, there will be active routes and inactive routes in the routing table. The router will then choose the best active route and place it in it's forwarding table. If there are equal-cost routes then Junos will place both routes in the forwarding table.

When a route is exported, only the active routes are exported.

## Routing Policy Building Blocks

A routing policy is made up of:

* **Policy Name**: A user-defined name that is referenced within the configuration
* **Term(s)**: User-defined if/then statements that contain from and then statments
* **From statements**: Specifies the match conditions based on one or more criteria
* **Then statements**: Specifies one or more actions to take if the from statement was matched

### From Statement Match Criteria

The 5 following criteria are used to match route policies:

* Next hop
* Prefix(es)
* Protocol(s)
* Route(s)
* Routing protocol attribute(s)

### Prefixes

The subnet prefix can either be from a prefix list or a route filter.

#### Prefix List

User-defined lists that contain one ore more subnet prefixes. The advantage of using a prefix-list is that they can be defined once and used in multiple places.

* Configure a prefix list

```bash
# Command
set policy-options prefix-list <name> <prefix>
# Example
set policy-options prefix-list Example-List 10.0.0.0/24
set policy-options prefix-list Example-List 10.0.1.0/24
```

* Verify a prefix list

```bash
# Command
show configuration policy-options
# Ouput
kameron@RE4> show configuration policy-options
prefix-list Example-List {
    10.0.0.0/24;
    10.0.1.0/24;
}
```

Prefix lists have two usage scenarios:

  1. When a route is referenced in a `prefix-list` statement, a route is matched only if it's exactly specified.
  2. When a route is referenced in a `prefix-list-filter` statement, you can use conditionals of `exact`, `longer`, or `orlonger`.

#### Route Filters

**Route Filters** cannot be used in multiple places and are instead defined within a single policy or policy term. Route filters are matched based on the following match types:

* `exact`: Only the exact prefix matches. Will not match any sub-prefixes. 192.168.0.0/16 only.
  * `from route-filter 192.168.0.0/16 exact`
* `orlonger`: Inclusively all sub-prefixes. 192.168.0.0/16 and below.
  * `from route-filter 192.168.0.0/16 or-longer`
* `longer`: Exclusively all sub-prefixes. Everything below 192.168.0.0/16
  * `from route-filter 192.168.0.0/16 longer`
* `upto`: Matches from 192.168.0.0/16 (inclusive) to 192.168.0.0/24 (Exclusive)
  * `from route-filter 192.168.0.0/16 upto /24`
* `prefix-length-range`: A range within a prefix. 192.168.0.0/20 to 192.168.0.0/24 within the 192.168.0.0/16 range.
  * `from route-filter 192.168.0.0/16 prefix-length-range /20-/24`

Route filters will match starting with the most specific entry going to the least specific entry.

### Example to redistribute static route in OSPF

```bash
kameron@RE4> show configuration policy-options
policy-statement default-route {
    term match-default-static-route {
        from {
            protocol static;
            route-filter 0.0.0.0/0 exact;
        }
        then accept;
    }

ospf {
    export default-route;
}

kameron@RE4> show route

inet.0: 18 destinations, 19 routes (18 active, 0 holddown, 0 hidden)
+ = Active Route, - = Last Active, * = Both

0.0.0.0/0          *[Access-internal/12] 6w6d 00:15:11, metric 0
                    > to 192.168.30.1 via fxp0.0
                    [OSPF/150] 00:33:20, metric 0, tag 0
                    > to 10.0.4.2 via ge-0/0/0.0
```

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
* [Policy Framework Overview](https://www.juniper.net/documentation/en_US/junos/topics/concept/policy-routing-overview.html)
