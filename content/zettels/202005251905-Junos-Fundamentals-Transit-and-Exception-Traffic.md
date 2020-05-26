---
title: "Junos Fundamentals: Transit and Exception Traffic"
date: 2020-05-25T19:05:27-05:00
draft: false
zettel: true
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id: 7
---
## Notes
### Transit Traffic
Transit traffic is any traffic that comes in an ingress port, checked against the forwarding table, and then forwarded out an egress port.

This type of traffic is your typical Unicast or Multicast traffic that comes in one port and is sent out either one port or multiple ports.

### Exception Traffic
Exception traffic is any traffic that requires some type of special handling. It is sent over the internal link to the RE and is given priority in the event of device congestion.

Since it is sent to the RE, it is rate-limited to prevent Denial-of-Service attacks. This rate is not configurable. 

Examples of this traffic include:

  * Packets addressed to the chassis such as routing protocol updates, SSH sessions, and pings.
	* IP packets with the IP options field, although this is rare
	* Traffic that requires the generation of ICMP messages.

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)

## Links
  * [Junos OS Fundamentals: Software Architecture](202005201440-Junos-Software-Architecture.md)
  * [Junos Fundamentals: Control and Forwarding Planes](202005251450-Junos-Fundamentals-Control-and-Forwarding-Planes.md)
  * [User Interfaces: CLI Modes](202005251910-User-Interfaces-CLI-Modes.md)
  * [User Interfaces: CLI Help](202005251940-User-Interfaces-CLI-Help.md)
  * [User Interfaces: CLI Navigation](202005251955-User-Interfaces-CLI-Navigation.md)
  * [User Interfaces: CLI Filtering Output](202005252000-User-Interfaces-CLI-Filtering-Output.md)