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

  1. Enter configuration mode:
      * `root@RE1> configure`
  2. Enter system configuration
      * `[edit]`
      * `root@RE1# edit system`
  3. Set the root password:
      * `[edit system]`
      * `root@RE1# set root-authentication plain-text-password`
  4. Set the hostname
      * `[edit system]`
      * `root@RE1# set host-name hostname`
  5. Set the time zone & system time
      * `[edit system]`
      * `root@RE1# set time-zone <timezone>`
      * `root@RE1# run set date YYYYMMDDhhmm.ss`
  6. Set the login methods
      * `[edit system]`
      * `root@RE1# set services ssh`
  7. Set the CLI session to timeout (it does not timeout by default)
      * `[edit system]`
      * `root@RE1# run set cli idle-timeout <0-100000 minutes>`
      * A setting of 0 will disable the timeout
  8. Set the login message
      * `[edit system]`
      * `root@RE1# set login message "<message>"`
  9. Commit the changes
      * `[edit system]`
      * `root@RE1# commit`
  10. Exit the configuration mode
      * `[edit system]`
      * `root@RE1# exit`
      * `[edit]`
      * `root@RE1# quit`

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
