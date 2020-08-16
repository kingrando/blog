---
title: "JNCIA-Junos | Junos Fundamentals: Control and Forwarding Planes"
date: 2020-05-25T14:51:08-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Routing Engine
Runs the control plane and is responsible for:

  * Layer 2 and Layer 3 protocol updates including BGP, OSPF, STP, etc…
  * System management including SNMP, SSH, Web GUI, etc…
  * Maintaining the bridging, forwarding, and routing tables.
  * Sending updated forwarding table information to the PFE via the dedicated internal link.
  * Software upgrades

## Packet Forwarding Engine
Runs the forwarding plane and is responsible for:

  * Forwarding transit traffic through the device.
  * Firewall filters, routing policies, and Class of Service (CoS)
  * Layer 2 and Layer 3 switching and forwarding via a dedicated piece of hardware called the Application-Specific Integrated Circuit (ASIC). The dedicated ASIC improves system performance.

Storing a locally cached copy of the forwarding table from the RE. This allows for faster decisions to be made regarding traffic and for traffic to still be forwarded if there are instability issues with the RE.

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)