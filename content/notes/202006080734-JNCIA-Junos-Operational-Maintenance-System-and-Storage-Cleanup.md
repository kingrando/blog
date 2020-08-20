---
title: "JNCIA Junos | Operational Maintenance and Monitoring: System and Storage Cleanup"
date: 2020-06-08T07:34:02-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Storage Clean-Up

Device storage can become cluttered with:

* Old log files
* Old software versions
* Temporary files

If it becomes cluttered then cleaning up the storage will be necessary. To do this you can issue the following command: `request system storage cleanup [dry-run]`.

## System Clean-Up

Cleaning up the system might be useful for system redeployment.

* To remove all configuration information on the RE and return the system to factory default and unlink all data files from their directories:
  * `request system zeroize`
* Also removes any traces of user-created files by scrubbing the memory and media.
  * `request system zeroize media`

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
