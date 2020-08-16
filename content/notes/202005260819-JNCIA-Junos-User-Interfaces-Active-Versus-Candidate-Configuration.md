---
title: "JNCIA-Junos | User Interfaces: Active Versus Candidate Configuration"
date: 2020-05-26T08:19:15-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Configuration Types
Junos OS uses an active/candidate version configuration system. The **active configuration** is the configuration that is running on the device at a given time. The **candidate configuration** is the configuration that a user is currently editing and has the potential to become the active configuration.

To move the candidate configuration to the active configuration you must issue the `commit` command. If there are no issues with the configuration then the commit command installs the candidate configuration as the active configuration.

To view the candidate configuration you can issue the `show` command under configuration mode. You can also check the configuration before committing it with the `commit check` command. 

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)