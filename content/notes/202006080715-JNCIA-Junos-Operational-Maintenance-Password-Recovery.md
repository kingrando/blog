---
title: "JNCIA Junos | Operational Maintenance and Monitoring: Password Recovery"
date: 2020-06-08T07:15:53-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Password Recovery

Passwords can be recovered on the device but only through a console connection. The ability to recover the password can be disabled by disallowing super user access using the `set system ports console insecure` command.

To reset the password, perform the following:

  1. Reboot the system.
  2. Press the spacebar when prompted.
  3. When the system shows the `loader>` then enter `boot -s` to enter single-user mode.
  4. Enter recovery mode: `recovery`
  5. Reset the root password.
     1. `configure`
     2. `set system root-authentication plain-text-password`
     3. `commit`
  6. Exit configuration mode.

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
