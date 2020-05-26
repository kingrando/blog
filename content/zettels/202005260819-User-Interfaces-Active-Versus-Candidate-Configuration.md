---
title: "User Interfaces: Active Versus Candidate Configuration"
date: 2020-05-26T08:19:15-05:00
draft: false
zettel: true
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id: 12
---
## Notes
Junos OS uses an active/candidate version configuration system. The active configuration is the configuration that is running on the device at a given time. The candidate configuration is the configuration that a user is currently editing and has the potential to become the active configuration.

To move the candidate configuration to the active configuration you must issue the `commit` command. If there are no issues with the configuration then the commit command installs the candidate configuration as the active configuration.

To view the candidate configuration you can issue the `show` command under configuration mode. You can also check the configuration before committing it with the `commit check` command. 

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)

## Links
  * [Junos OS Fundamentals: Software Architecture](202005201440-Junos-Software-Architecture.md)
  * [Junos Fundamentals: Control and Forwarding Planes](202005251450-Junos-Fundamentals-Control-and-Forwarding-Planes.md)
  * [Junos Fundamentals: Transit and Exception Traffic](202005251905-Junos-Fundamentals-Transit-and-Exception-Traffic.md)
  * [User Interfaces: CLI Modes](202005251910-User-Interfaces-CLI-Modes.md)
  * [User Interfaces: CLI Help](202005251940-User-Interfaces-CLI-Help.md)
  * [User Interfaces: CLI Navigation](202005251955-User-Interfaces-CLI-Navigation.md)
  * [User Interfaces: CLI Filtering Output](202005252000-User-Interfaces-CLI-Filtering-Output.md)
  * [User Interfaces: Reverting to Previous Configuration](202005260853-User-Interfaces-Reverting-to-Previous-Configuration.md)
  * [User Interfaces: Adding and Removing Configuration Statements](202005260858-User-Interfaces-Adding-Removing-Configuration-Statements.md)
  * [User Interfaces: The J-Web Interface](202005260903-User-Interfaces-J-Web-Interface.md)