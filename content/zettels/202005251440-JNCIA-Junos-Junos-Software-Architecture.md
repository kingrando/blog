---
title: "JNCIA-Junos | Junos OS Fundamentals: Software Architecture"
date: 2020-05-25T14:41:01-05:00
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
## Compenents
  * Junos is a hardened and customized version of FreeBSD.
  * Composed of  the Routing Engine (Control Plane) and the Packet Forwarding Engine (Forwarding Plane).
  * Compartmentalized architecture in which each process is in it's own protected memory space. This prevents one process from interfering with the operation of another.

## Platforms
  * Each platform within the Junos OS family (EX, MX, QFX, SRX, etc...) runs on the same software base.
  * The software base is broken down into three trains:
    * **The X Release**: Security focused and implements security enhancements. Released faster than the other two trains and is designed for security focused platforms such as the SRX.
    * **The R Release**: Maintenance focused and does not implement new features, only bug fixes.
    * **The F Release**: A feature focused release that implements new content, features, and bug fixes. Eventually merged to the R release.

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)