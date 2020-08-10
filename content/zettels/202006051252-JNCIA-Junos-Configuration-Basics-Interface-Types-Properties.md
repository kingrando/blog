---
title: "JNCIA Junos | Configuration Basics: Interface Types & Properties"
date: 2020-06-05T12:52:30-05:00
draft: false
type: "zettel"
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id:
  - "2"
---
## Interface Types
There are 5 primary interface types on Junos devices:

  * Management
    * Used to connect the device to an out of band (OOB) management network.
    * The naming of these interfaces is platform-specific, but examples include `fxp0` and `me0`.
  * Internal
    * Used to connect the control plane and the forwarding plane together.
    * The naming of these interfaces is platform-specific, but examples include `fxp1` and `em0`.
  * Network
    * Used to provide media connectivity.
    * Examples include `ae` (Aggregated Ethernet), `fe` (Fast Ethernet), `ge` (Gigabit Ethernet), and `xe` (10G ethernet).
  * Services
    * Provide user-configurable services that are used to manipulate traffic before being delivered to the destination.
    * Services can be provided either through Physical Interface Cards (PICs) or through software.
    * Examples include `es` (encryption), `gr` (GRE tunnel), `ip` (IP-over-IP encapsulation), and `mo` (passive monitoring interface). 
  * Loopback
    * Provides a hardware independent interface.
    * Uses the `lo0` destination on all platforms.

### Interface Naming
Interface naming typically follows the convention of `(Interface Media Type)-(Line Card Slot Number)/(Interface Slot Card Number)/(Port Number)`

Examples:

  * `ge-0/0/1`
  * `xe-1/1/1`

## Logical Units
Juniper interfaces can be subdivided from a single physical interface into multiple logical interfaces. This is a similar concept to Cisco's sub-interfaces. The difference is that all Juniper interfaces must have a logical unit number. This number is typically 0. 

Encapsulation methods such as PPP and Cisco HDLC only support one logical interface and it must be 0.

Other encapsulation methods such as Frame Relay, ATM, and 802.1Q support multiple logical units.

**Note**: Logical unit numbers are separate in meaning from circuit identifiers and do not need to match. It is suggested to keep them the same though to aid in troubleshooting.

## Multiple Addresses
By default, when you attempt to change an IP address on a Juniper device it will actually add an additional IP address to that interface. This would be done using the command: 
  * `set family inet address <ip-address/mask>`

However, to actually change the IP address on an interface you must use the rename command and not the set command as shown: 
  * `rename family inet address <ip-address/mask> to address <ip-address/mask>`

## Interface Properties
There are two types of interface properties: *physical* and *logical*. 

The *Physical Interface* properties are those that define physical characteristics about the interface such as:

  * Data Link Layer protocol and keepalives
  * **Link Mode**: Full or Half-duplex
  * Speed
  * MTU
  * **Clocking**: Internal or External
  * **Scrambling**: Payload scrambling
  * **Frame Check Sequence (FCS)**: Default is 16-bit but can be 32-bit
  * **Diagnostic characteristics**: Enable local or remote loopbacks or setup a bit error rate test (BERT)

The *Logical Interface* properties are those that describe the more abstract items such as:

  * **Protocol family**: inet, inet6, iso, mpls, or bridge
  * Addresses
  * **Virtual circuits**: Data-link connection identifier (DLCI), Virtual Path Identifier (VPI), Virtual Channel Identifier (VCI), or VLAN tag
  * **Other characteristics**: Inverse ARP, traps, accounting profiles

## Interface Configuration
  * Create an interface:
    * `set interfaces <interface-name> unit <unit-number>`
  * Assign an IP address
    * `set interfaces <interface-name> unit <unit-number> family inet address <ip-address/prefix-length>`
  * Set a description
    * `set interfaces <interface-name> unit <unit-number> description <description>`
  * Set VLAN ID
    * `set interfaces <interface-name> unit <unit-number> vlan-id <vlan-id>`

## Interface Verification
  * Show operational information regarding interface:
    * `show interfaces`
    * **Note**: If ran in configuration mode, it will display the configuration of that interface.
  * Show an abbreviated list of interfaces including admin, link-state status, protocol, and IP address.
    * `show interfaces terse`
  * Show detailed information about an interface including status, physical characteristics, and traffic counters.
    * `show interfaces detail`
  * Show extensive information about an interface including output from `show interfaces detail` plus error counters.
    * `show interfaces extensive`
  * Show descriptions for interfaces
    * `show interfaces descriptions`

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
