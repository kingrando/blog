---
title: "JNCIA Junos | Configuration Basics: Rescue Configuration"
date: 2020-05-27T08:49:57-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Rescue Configuration
With Junos OS a rescue configuration can be created which will be loaded in the event there is an issue with the active configuration. 

By default there is no rescue configuration created.

To create a rescue configuration a root password must be set. It's also advised to configure everything you would need for network connectivity as well. 

  * To set a configuration as the resuce configuration issue the following command:
    * `root@RE1> request system configuration rescue save`
  * To delete the rescue configuration, issue the following command:
    * `root@RE1> request system configuration rescue delete`
  * To load the active rescue configuration:
    * `root@RE1# rollback rescue`
    * `root@RE1# commit`
  * To view the rescue configuration, issue the following command:
    * `root@RE1> show system configuration rescue`


## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)