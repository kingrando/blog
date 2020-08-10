---
title: "JNCIA Junos | Routing Policy and Firewall Filters: Firewall Filters"
date: 2020-07-04T08:14:27-05:00
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
## What are Firewall Filters?
Firewall filters (ACLs in Cisco world) enable you to control the traffic into and out of your network. 

There are two types of firewall filters: stateless and stateful. 

  * Junos firewall filters are *stateless* in nature meaning that each packet is individually inspected. Since there are no concept of state or connections, a rule must be created for both directions. 
  * Stateful firewalls, on the other hand, can create entries in a state table and dynamically create return rules for traffic. Modern firewalls such as the Cisco ASA are stateful firewalls.

A stateless firewall is primarily used to increase the security of the Routing Engine. 

## Traffic Flow
Firewall filters affect the flow of traffic entering (ingress) or exiting (egress) the device.
  
  * *Ingress filters* affect traffic that flows either into an interface on the device or traffic that is destined for the Routing Engine.
  * *Egress filters* affect traffic that flows out of an interface and does not affect any traffic that goes to the Routing Engine.

## Filter Components
A firewall filter is made up of the following components:

  * **Firewall Filter Family**: This specifies the protocol family the firewall filter should apply for.
    * This is under the `firewall` hierarchy using the `set family <family-name>` command. 
    * Possible values are:
      * `any`
      * `bridge`
      * `ccc`
      * `evpn`
      * `inet`
      * `inet6`
      * `mpls`
      * `vpls`
  * **Firewall Filter Type**: This specifies the type of filter to use.
    * This is set under the `firewall family <family-name>` hierarchy using the `set filter <filter-name>` command.
    * Possible values are:
      * **Standard**: Filters based on either *any* or a protocol.
        * Set under the `firewall family <family-name>` hierarchy with the `set filter <filter-name>` command.
      * **Service**: Filters ingress and egress IPv4 and IPv6 traffic based on almost any field of the IP header.
        * Set under the `firewall family [inet | inet6]` hierarchy with the `set service-filter <filter-name>` command.
      * **Simple**: Filters ingress on IPv4 traffic using Source/Destination IP address and ports.
        * Set under the `firewall family inet` hierarchy with the `set simple-filter <filter-name>` command.
    * **Terms**: Terms contain the match conditions and actions.
      * **Match Condition**: The *from* statement contains what should be matched. 
      * **Action**: The *then* statement contains the action to take once the condition has been matched. There are three types of actions:
        * **Terminating Actions**: Performs the action and then halts any more processing of the packet.
        * **Non-terminating Actions**: Performs stuff such as counting packets, logging information, or sampling packets.
        * **Flow Control Actions**: Enables the next term to be evaluated instead of performing a terminating action.

## Application
Once a firewall filter has been configured, you must apply it to an application point. Application points include:

  * Logical interfaces
  * Physical interfaces
  * Loopback interfaces

To apply firewall filters use the following command(s) at the interface hierarchy:

  * Standard Firewall Filter:
    * `[edit interfaces ge-0/0/0 unit 0]` or `[edit interfaces ge-0/0/0 unit 0 family inet]`
    * `set filter [input | input-filter-list | output | output-filter-list ] <filter-name>`    
  * Service Filter:
    * `[edit interfaces ge-0/0/0 unit 0 family inet]`
    * `set service input post-service-filter <filter-name>`
  * Simple Firewall Filter:
    * `[edit interfaces ge-0/0/0 unit 0 family inet]`
    * `set simple-filter <filter-name>`

## Policing

Firewall filters can apply rate policing and limiting to traffic that you would like to control. These filters can be based on addressees, protocols, or ports. Policing employs the token-bucket algorithm, which enforces a limit on average bandwidth while allowing bursts up to a specified maximum value. 

Rate limits can be applied to bandwidth or the maximum burst size. Bandwidth can be policed either using the bandwidth limit in bits per second or it can be done using a percentage. Burst size is in bytes and is the total number of bytes the system allows in bursts of data that exceed the given bandwidth limit.

An example for configuring a policer you use the following commands at the `firewall` hierarchy:

  * `[edit firewall]`
  * `set policer Example-Policer logical-bandwidth-policer if-exceeding bandwidth-percent 75`
  * `set policer Example-Policer then discard`  

## Unicast RPF Check
Unicast Reverse Path-Forwarding (RPF) checks automate anti-spoofing filters based on routing tables, which helps to validate packet receipt on the interfaces.

The two types of Unciast RPF Checks are:
  * **Strict (Default)**: The system expects to receive traffic on a given interface if it has an active route to the packet's source address and if it received the packet on the interface that is the next hop for the active route to the packet's source address.
  * **Loose**: Checks only to ensure a valid route to the source address exists in the routing table.

There are a few caveats with Unicast RPF checks: 

  1. When you have asymmetric routes, uRPF could cause legitimate traffic to be dropped. You want to use the feasible-paths option to consider all paths and not just the active routes
  2. Typically only want to enable on the edge device in the network and not on all network devices in your network.
  3. A packet is discarded by default if it fails the RPF check. You can bypass this by using the fail-filter. The fail-filter is required to permit DHCP or BOOTP traffic denied by RPF
 
To configure RPF Check:
  * Reverse packet forwarding (RPF) check filter:
    * `[edit interfaces ge-0/0/0 unit 0 family inet]`
    * `set rpf-check fail-filter <filter-name>`
	
## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)

