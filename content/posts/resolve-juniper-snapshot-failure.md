---
title: "Resolving A Junos Snapshot Failure"
date: 2020-09-19T3:00:00-00:00
draft: false
---

## Overview

In this post I'm going to go over how to resolve the error message seen under `show system snapshot media internal all-members` that indicates the alternate partition cannot be mounted.

On dual-oot partitioned Juniper devices there is an active slice, which contains the running software and configuration, and an alternate slice, which contains a backup of the software and configuration. When you upgrade Junos the active

If you do not have `auto-snapshot` turned on, occasionally the attempt to backup the active configuration and software from the active partition to the alternate partition will fail. To verify if this fails you can run the command `show system snapshot media internal all-members` and it will display all the active and alternate partitions for the router, switch, or virtual chassis. Below is a what a properly snapshot chassis will look like.

```bash
kameron@SW1> show system snapshot media internal all-members
fpc0:
--------------------------------------------------------------------------
Information for snapshot on       internal (/dev/da0s1a) (backup)
Creation date: Apr 30 00:43:19 2020
JUNOS version on snapshot:
  jbase  : ex-12.3R12-S15
  jkernel-ex-3300: 12.3R12-S15
  jcrypto-ex: 12.3R12-S15
  jdocs-ex: 12.3R12-S15
  jswitch-ex: 12.3R12-S15
  jweb-ex: 12.3R12-S15
  jpfe-ex33x: 12.3R12-S15
  jroute-ex: 12.3R12-S15
  fips-mode-arm: 12.3R12-S15
Information for snapshot on       internal (/dev/da0s2a) (primary)
Creation date: Sep 1 08:25:17 2020
JUNOS version on snapshot:
  jbase  : ex-12.3R12-S15
  jkernel-ex-3300: 12.3R12-S15
  jcrypto-ex: 12.3R12-S15
  jdocs-ex: 12.3R12-S15
  jswitch-ex: 12.3R12-S15
  jweb-ex: 12.3R12-S15
  jpfe-ex33x: 12.3R12-S15
  jroute-ex: 12.3R12-S15
  fips-mode-arm: 12.3R12-S15
```

If the there is an issue with the snapshot you will typically see a message similar to this:

```bash
kameron@SW1> show system snapshot media internal all-members
fpc0:
--------------------------------------------------------------------------
Information for snapshot on       internal (/dev/da0s1a) (backup)
Creation date: Apr 30 00:43:19 2020
JUNOS version on snapshot:
  jbase  : ex-12.3R12-S15
  jkernel-ex-3300: 12.3R12-S15
  jcrypto-ex: 12.3R12-S15
  jdocs-ex: 12.3R12-S15
  jswitch-ex: 12.3R12-S15
  jweb-ex: 12.3R12-S15
  jpfe-ex33x: 12.3R12-S15
  jroute-ex: 12.3R12-S15
  fips-mode-arm: 12.3R12-S15
error: cannot mount /dev/da0s2a
```

This error usually occurs because the partition `/dev/da0s2a` is already mounted. If you run the command `show log snapshot` you will see a message that says `mount: /dev/da0s2a : Operation not permitted`. To resolve this, we need to do the following:

## Resolution

To resolve this, you must connect to the device (router or switch) that is having the issue. If it's a virtual chassis, then you must connect to the virtual chassis member.

### Single Member Resolution

```bash
### Connect to the device and start the shell ###
kameron@SW1> start shell
%

### Change user to root ###
su root
Password:
kameron@SW1:RE:0%

### Unmount the altroot ###
kameron@SW1:RE:0% umount /altroot

### Go back to the Junos CLI ###
kameron@SW1:RE:0% exit
exit
% exit
exit

### Rerun the snapshot ###
kameron@SW1> request system snapshot slice alternate
```

### Multi-Member Virtual Chassis

For a virtual chassis the above steps remain the same except you need to connect to the specific member first. To connect to s specific member run the following command:

```bash
### Open a session to a specified member ###
kameron@SW1> request session member 2
{linecard:2}
kameron@SW1>

### Connect to the device and start the shell ###
kameron@SW1> start shell
%

### Change user to root ###
su root
Password:
kameron@SW1:RE:0%

### Unmount the altroot ###
kameron@SW1:RE:0% umount /altroot

### Go back to the Junos CLI ###
kameron@SW1:RE:0% exit
exit
% exit
exit

### Rerun the snapshot ###
kameron@SW1> request system snapshot slice alternate
```

Once the above steps are run either in a single member of mutli-member chassis you should have both partitions correctly configured with snapshots.

I do advise ensuring the configuration `system auto-snapshot` is in your confiugration. This should prevent this error from occuring. When the system reboots, the snapshot feature will copy the alternate root partition to the primary root parition.

If you have any questions or you see anything that might be inaccurate, feel free to reach out to me through email or twitter so I can update it.

## References

* [Juniper: Example: Taking a Snapshot of the Software and Configuration](https://www.juniper.net/documentation/en_US/junos/topics/example/request-system-snapshot-scenarios.html)
* [Juniper: auto-snapshot](https://www.juniper.net/documentation//en_US/junos/topics/reference/configuration-statement/auto-snapshot-edit-system.html)
