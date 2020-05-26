---
title: "Junos OS Fundamentals: Software Architecture"
date: 2020-05-25T14:41:01-05:00
draft: false
zettel: true
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id: 5
---
## Notes
  * Junos is a hardened and customized version of FreeBSD.
  * Composed of  the Routing Engine (Control Plane) and the Packet Forwarding Engine (Forwarding Plane).
  * Compartmentalized architecture in which each process is in it's own protected memory space. This prevents one process from interfering with the operation of another.
  * Each platform within the Junos OS family (EX, MX, QFX, SRX, etc...) runs on the same software base.
  * The software base is broken down into three trains:
    * **The X Release**: Security focused and implements security enhancements. Released faster than the other two trains and is designed for security focused platforms such as the SRX.
    * **The R Release**: Maintenance focused and does not implement new features, only bug fixes.
    * **The F Release**: A feature focused release that implements new content, features, and bug fixes. Eventually merged to the R release.

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)

## Links
  * [Junos Fundamentals: Control and Forwarding Planes](202005201450-Junos-Fundamentals-Control-and-Forwarding-Planes.md)
  * [Junos Fundamentals: Transit and Exception Traffic](202005251905-Junos-Fundamentals-Transit-and-Exception-Traffic.md)
  * [User Interfaces: CLI Modes](202005251910-User-Interfaces-CLI-Modes.md)
  * [User Interfaces: CLI Help](202005251940-User-Interfaces-CLI-Help.md)
  * [User Interfaces: CLI Navigation](202005251955-User-Interfaces-CLI-Navigation.md)
  * [User Interfaces: CLI Filtering Output](202005252000-User-Interfaces-CLI-Filtering-Output.md)
  * [User Interfaces: Active versus Candidate Configuration](202005260819-User-Interfaces-Active-Versus-Candidate-Configuration.md)
  * [User Interfaces: Reverting to Previous Configuration](202005260853-User-Interfaces-Reverting-to-Previous-Configuration.md)
  * [User Interfaces: Adding and Removing Configuration Statements](202005260858-User-Interfaces-Adding-Removing-Configuration-Statements.md)
  * [User Interfaces: The J-Web Interface](202005260903-User-Interfaces-J-Web-Interface.md)