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

If a setting is explicited configured at a configuration hierarchy and there is a group applied to the hierarchy, the explicit configuration will take precedence.

A configuration item can have multiple groups applied to it but only one apply-groups statement can be set for it. The groups should be ordered in preference of priority: `apply-groups group1 group2`.

## Configuration
  * Create a group
    * `set groups <group-name>`
  * Change to the specific heirarchy and apply the group
    * `set apply-groups <group-name>`

## Verification
  * Display the configured group
    * `show configuration groups`
  * Display the applied groups
    * `show configuration configuration-item apply-groups`
      * Example: `show configuration interfaces ge-0/0/0 apply-groups`

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
