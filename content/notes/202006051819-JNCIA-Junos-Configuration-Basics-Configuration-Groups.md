---
title: "JNCIA Junos | Configuration Basics: Configuration Groups"
date: 2020-06-05T18:19:09-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Configuration Groups

Configuration groups are a way to create a set of configuration statements, or a template, and then apply those settings to multiple portions of the configuration. The configuration statements are inherited by the configuration where they are referenced. This allows you to make changes to the configuration group and then those changes are replicated to the child objects.

If a setting is explictly configured at a configuration hierarchy and there is a group applied to the hierarchy, the explicit configuration will take precedence.

A configuration item can only have one apply-group statement set for it, but that apply-group statement can contain multiple configuration groups. The groups should be ordered in preference of priority: `apply-groups group1 group2`.

## Configuration

* Create a group

  ```bash
  # Command
  set groups <group-name>
  # Example
  set groups ExampleGroup1
  ```

* Change to the specific hierarchy and apply the group

  ```bash
  # Command
  set apply-groups <group-name>
  # Example
  set apply-groups ExampleGroup1
  ```

## Verification

* Display the configured group

  ```bash
  # Command
  [edit]
  show groups
  # Output
  [edit]
  kameron@RE4# show groups ExampleGroup1
  system {
      host-name Example-Hostname;
  }
  ```

* Display the applied groups

  ```bash
  # Command
  [edit]
  show apply-groups
  # Output
  [edit]
  kameron@RE4# show apply-groups
  ## Last changed: 2020-08-21 17:57:47 CDT
  apply-groups [ ExampleGroup1 ];
  ```

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
