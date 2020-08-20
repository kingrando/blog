---
title: "JNCIA Junos | Operational Monitoring and Maintenance: Junos Installation and Upgrade"
date: 2020-06-06T12:32:16-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Junos Naming Convention

The Junos OS has the following naming convention: `package-name-m.nZx-distribution.tgz`

The naming convention can be broken down as follows:

* `package-name`:
  * `jinstall*`: Used on M, T, and MX Series devices
  * `jinstall-ex*`: Used on EX series devices
  * `junos-install*`: Used on MEX and EX series devices that support Junos OS with the upgraded FreeBSD
  * `junos-srx*`: Used on SRX series devices
* `m.z`
  * The major and minor release number
* `Z`
  * The Type of Junos release such as `R` for released or `B` for beta.
* `z.y`
  * The build and spin number such as `19.2`
* `distribution`
  * Either `domestic` for US and Canada or `export` used for worldwide use.

## Upgrading Junos OS

To prevent a Junos OS device from unauthorized activity or software, each Junos image is digitally signed with a manifest of registered executables. If the firmware is missing this fingerprint, Junos will not run the software.

The Junos OS can be upgraded either by downloading the version directly from the Juniper support site and copying over the firmware or by using the built-in Junos OS FTP client. The FTP client allows you to download the OS directly onto the device.

When copying the firmware over to the device it is recommended to store it in the `/var/tmp` directory. Although done during a regular installation, this directory can be cleaned up using the command: `request system storage cleanup [dry-run]`. You can use the `dry-run` option to determine what files would be removed before removing them.

To upgrade the OS, issue the following command: `request system software add path/image-name [reboot]`. To complete the installation the device must be rebooted. This can be done manually with the command `request system reboot` or it can be done automatically during the installation by using the `reboot` option at the end of the `request system software add` command.

## Unified In-Service Software Upgrade (ISSU)

Unified ISSU allows you to upgrade between two different Junos OS versions without interruption to the control plane. This eliminates the need for downtime during software upgrade therefore reducing operational costs and delivering higher service levels.

This feature is only available on dual Routing Engine (RE) devices.

The process to perform an ISSU is:

  1. Enable Graceful Routing Engine Switchover (GRES) and Nonstop Active Routing (NSR).
  2. Verify the Routing Engines (REs) and protocols are synchronized.
  3. Download the new software package.
  4. Copy the software package to the device.
  5. Issue the command `request system software in-service-upgrade` on the master RE.

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
