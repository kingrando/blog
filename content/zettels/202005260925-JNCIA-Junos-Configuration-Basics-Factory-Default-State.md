---
title: "JNCIA-Junos | Configuration Basics: Factory Default State"
date: 2020-05-26T09:25:55-05:00
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
## Notes
When a device ships, it ships with a factory-default configuration. This default configuration contains a few things:
  * There is a root account that has no password. When you first log into a Junos OS device you will log in with root as the username and no password and you will be taken directly to the UNIX shell.
  * The system host name will not be set and instead will say Amnesiac.
  * System logging will be enabled.

Before any configuration can be committed, a root password must be set. This can be done using the following command:

  * `set system root-authentication plain-text-password`

If you need to restore a device to factory-default configuration, you can enter these commands:

```nix
  load factory-default
  set system root-authentication plain-text-password
```

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)