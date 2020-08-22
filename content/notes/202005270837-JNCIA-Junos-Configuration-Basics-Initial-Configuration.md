---
title: "JNCIA Junos | Configuration Basics: Initial Configuration"
date: 2020-05-27T08:37:55-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Initial Configuration Recommendation

Juniper recommends configuring the following  items when you are first setting up your Junos OS device:

* The root password
* Hostname
* System time
* Remote access protocols
* Management interface and static routes for the management traffic to use the management interface

**Note**: I have labeled my Junos OS devices in my lab as RE1 through RE5 so the hostnames in my commands will reflect that.

## Configure System Parameters

Perform the following steps:

```bash
# 1. Enter configuruation Mode
kameron@RE4> configure

# 2. Enter system-level hierarchy
[edit]
kameron@RE4# edit system

# 3. Set the root password
[edit system]
kameron@RE4# set root-authentication plain-text-password
New password:
Retype new password:

# 4. Set the hostname
[edit system]
kameron@RE4# set host-name Example-Name

# 5. Set the time zone
[edit system]
kameron@RE4# set time-zone America/Chicago

# 6. Set the date & time
[edit system]
kameron@RE4# run set date 202008220828.00

# 7. Set the login methods
[edit system]
kameron@RE4# set services ssh

#8. Set the CLI session idle timeout (Not configured by default, 0 disables the timeout)
[edit system]
kameron@RE4# run set cli idle-timeout <0-100000 minutes>

#9. Set the login message
[edit system]
kameron@RE4# set login message "This is my router message"

# 10. Commit the changes
[edit system]
kameron@RE4# commit

# 11. Exit the configuration mode
[edit system]
kameron@RE4# exit
[edit]
kameron@RE4# quit
```

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
