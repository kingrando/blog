---
title: "JNCIA-Junos | User Interfaces: Reverting to Previous Configuration"
date: 2020-05-26T08:53:42-05:00
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
## Configuration Rollback
Junos can store the last 50 configurations, numbered 0 to 49, 0 being the active configuration with 49 previous configurations. 

This enables you to roll back to a previous configuration. 

To roll back to a previous configuration you must issue the `rollback n` command, `n` being the configuration number.

When you are making a change and want to undo the changes you have made you can issue the `rollback 0` command and it will roll the candidate configuration back to the active configuration.

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)