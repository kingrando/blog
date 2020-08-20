---
title: "JNCIA-Junos | User Interfaces: Adding Removing Configuration Statements"
date: 2020-05-26T08:58:22-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Editing the Configuration

Configuration statements are the actual contents of the configuration files. An example is:

```bash
interfaces {
    ge-0/0/0 {
        unit 0 {
            family inet {
                address 10.0.1.1/30;
            }
        }
    }
}
```

The following commands are used to modify configuration statements:

* `set` - Adds configuration statements
* `delete` - Removes commands that were added with the set command. Returns to the default condition.
* `deactivate` - Causes the specified configuration hierarchy to be ignored while retaining the original configuration.
* `active` - Places the deactivated command back into effect.

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
