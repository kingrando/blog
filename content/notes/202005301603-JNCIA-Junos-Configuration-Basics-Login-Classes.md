---
title: "JNCIA Junos | Configuration Basics: Login Classes"
date: 2020-05-30T16:03:23-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Login Classes

Junos OS contains four predefined login classes:

* **Operator**: Grants the permission flags for clear, network, reset, trace, and view
* **Read-Only**: Grants the permission flags for view
* **Super-User** or **Superuser**: Grants the permission flag for all
* **Undefined**: Grants the permission flag for None

Custom login classes can be set which grant the ability to:

* Define what equipment a user has access to
* Define what commands or statements a user can run
* Define the idle timeout for a user's session.

To define a custom login class, perform the following:

* `set system login class <class-name>`
* `set system login class <class-name> <settings>`

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
