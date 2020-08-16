---
title: "JNCIA Junos | Operational Monitoring and Maintenance: Powering On and Shutting Down Devices"
date: 2020-06-08T07:08:43-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Powering On and Off Devices
Junos OS devices work differently than other competitor devices such as Cisco. Since Junos OS is based on FreeBSD and Linux, devices require a graceful shutdown to be performed. If a graceful shutdown is not performed, you risk corrupting the OS or configuration. If the OS or configuration becomes corrupted, then it will need to be reinstalled and configured.

To perform a graceful shutdown issue the following command:

  * `request system halt`

If a device has redundant routing engines, issue the following command on the master:

  * `request system halt both-routing-engines`
	
If switches are in a stack (virtual chassis), issue the following command on the master:

  * `request system halt all-members`

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
