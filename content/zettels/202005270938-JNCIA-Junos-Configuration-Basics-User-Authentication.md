---
title: "JNCIA Junos | Configuration Basics: User Authentication"
date: 2020-05-27T09:38:44-05:00
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
Junos OS provides three methods for authenticating users: Local accounts, RADIUS, and TACACS+.

### Local Accounts
All new users that are created locally are added under the `[edit system login]` hierarchy.

```nix
system {
    login {
        user kameron {
            uid 2000;
            class super-user;
            authentication {
                encrypted-password ""; ## SECRET-DATA
            }
        }
```
## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)