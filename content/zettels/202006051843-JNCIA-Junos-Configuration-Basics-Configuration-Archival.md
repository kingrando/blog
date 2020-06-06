---
title: "JNCIA Junos | Configuration Basics: Configuration Archival"
date: 2020-06-05T18:43:57-05:00
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
## Configuration Files
Configurations can be archived and backed up to a separate device. 

Configurations queued for transmission are stored in the `/var/transfer/config`

Successful configuration transfers are logged in `/var/log/messages`

The destination filename is saved in the following format, where n corresponds to the number of the compressed configuration rollback file that has been archived:

  * `<router-name>_YYYYMMDD_HHMMSS_juniper.conf.n.gz`

## Configuration
  * Configure the archival sites (HTTP, FTP, or SCP)
    * `set system archival configuration archive-sites url`
  * Configure the transfer interval
    * `set system archival configuration transfer-interval 15-2880minutes`
  * Configure the option to transfer on commit
    * `set system archival configuration transfer-on-commit`

## Verification
  * List files queued up for archive transfer
    * `show system configuration archival`

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)