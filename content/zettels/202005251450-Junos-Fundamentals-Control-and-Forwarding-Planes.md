---
title: "Junos Fundamentals: Control and Forwarding Planes"
date: 2020-05-25T14:51:08-05:00
draft: true
zettel: true
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id: 6
---
## Notes
The control plane runs on the Routing Engine and the Forwarding Plane runs on the Packet Forwarding Engine.

### Routing Engine
The Routing Engine is responsible for:

  * Layer 2 and Layer 3 protocol updates including BGP, OSPF, STP, etc…
  * System management including SNMP, SSH, Web GUI, etc…
  * Maintaining the bridging, forwarding, and routing tables.
  * Sending updated forwarding table information to the PFE via the dedicated internal link.
  * Software upgrades

### Packet Forwarding Engine
The forwarding plane is responsible for:

  * Forwarding transit traffic through the device.
  * Firewall filters, routing policies, and Class of Service (CoS)
  * Layer 2 and Layer 3 switching and forwarding via a dedicated piece of hardware called the Application-Specific Integrated Circuit (ASIC). The dedicated ASIC improves system performance.

Storing a locally cached copy of the forwarding table from the RE. This allows for faster decisions to be made regarding traffic and for traffic to still be forwarded if there are instability issues with the RE.


## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)

## Links
  * [Junos OS Fundamentals: Software Architecture](202005201440-Junos-Software-Architecture.md)
  * [Junos Fundamentals: Transit and Exception Traffic](202005251905-Junos-Fundamentals-Transit-and-Exception-Traffic.md)
  * [User Interfaces: CLI Modes](202005251910-User-Interfaces-CLI-Modes.md)
  * [User Interfaces: CLI Help](202005251940-User-Interfaces-CLI-Help.md)
  * [User Interfaces: CLI Navigation](202005251955-User-Interfaces-CLI-Navigation.md)
  * [User Interfaces: CLI Filtering Output](202005252000-User-Interfaces-CLI-Filtering-Output.md)
  * [User Interfaces: Active versus Candidate Configuration](202005260819-User-Interfaces-Active-Versus-Candidate-Configuration.md)
  * [User Interfaces: Reverting to Previous Configuration](202005260853-User-Interfaces-Reverting-to-Previous-Configuration.md)
  * [User Interfaces: Adding and Removing Configuration Statements](202005260858-User-Interfaces-Adding-Removing-Configuration-Statements.md)
  * [User Interfaces: The J-Web Interface](202005260903-User-Interfaces-J-Web-Interface.md)