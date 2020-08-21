---
title: "JNCIA Junos | Configuration Basics: Configuration Archival"
date: 2020-06-05T18:43:57-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Configuration Files

Configurations can be archived and backed up to a separate device.

Configurations queued for transmission are stored in the `/var/transfer/config`

Successful configuration transfers are logged in `/var/log/messages`

The destination filename is saved in the following format, where n corresponds to the number of the compressed configuration rollback file that has been archived:

* `<router-name>_YYYYMMDD_HHMMSS_juniper.conf.n.gz`

## Configuration

* Configure the archival sites (HTTP, FTP, or SCP)

  ```bash
  # Command
  set system archival configuration archive-sites <url>
  # Example
  set system archival configuration archive-sites ftp://10.0.0.1
  ```

* Configure the transfer interval

  ```bash
  # Command
  set system archival configuration transfer-interval <15-2880 minutes>
  # Example
  set system archival configuration transfer-interval 60
  ```

* Configure the option to transfer on commit

  ```bash
  # Command
  set system archival configuration transfer-on-commit
  ```

## Verification

* List files queued up for archive transfer

  ```bash
  # Command
  [edit]
  show system archival
  # Output
  [edit]
  kameron@RE4# show system archival
  configuration {
      transfer-interval 60;
      archive-sites {
          ftp://10.0.0.1;
      }
  }
  ```

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
