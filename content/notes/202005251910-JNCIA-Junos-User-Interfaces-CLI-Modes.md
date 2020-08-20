---
title: "JNCIA-Junos | User Interfaces: CLI Modes"
date: 2020-05-25T19:12:08-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Entering the CLI

The CLI can be entered either through Out-of-Band Management Serial Port, Out-of-Band Management Ethernet port, or In-band SSH/Telnet.

If you connect to through any of these options and login as the `root` user then you will need to enter the command `cli` to enter the Junos CLI. To exit the Junos CLI and get back to the Unix shell you can enter `start shell`.

* Enter Junos CLI from Unix CLI: `cli`
* Enter Unix CLI from Junos CLI: `start shell`

The Junos OS has two modes for working with the command-line, Operational Mode and Configuration Mode.

## Operational Mode

Operational mode is the default mode you enter after logging into the device as a non-root user.

This mode is used for device monitoring and troubleshooting.

Common commands that are used here are:

* `configure` - Enters configuration mode
* `help` - Provide help information about commands
* `monitor` - Show real-time debugging information
* `ping` - Ping remote target
* `show` - Show system information
* `test` - Perform diagnostic debugging
* `traceroute` - Trace route to remote host

## Configuration Mode

Configuration mode is used to change the configuration of a Junos OS device. It is accessed by typing `configure` under operational mode.

Common commands used under this mode are:

* `activate` - Remove the inactive tag from a statement
* `commit` - Commit current set of changes
* `deactivate` - Add the inactive tag to a statement
* `delete` - Delete a data element
* `edit` - Edit a sub-element
* `rollback` - Roll back to a previous committed configuration
* `run` - Run an operational-mode command
* `set` - Set a parameter
* `show` - Show a parameter

Junos OS allows for multiple users to be in the configuration mode and by default (using just the configure command) can make changes to the configuration.

When users enter configuration mode with the `configure` command they have the following access:

* No locking of the configuration and all users can change the configuration
* Most recent changes are committed when the commit change is issued
* All users can commit the configuration
* When a user issues commit, all changes that have been made are committed including yours.

When users enter configuration mode with the `configure private` command they have the following access:

* Multiple users can edit the configuration at the same time, but each user has their own candidate configuration that they can make independent changes to.
* If the same configuration has been changed by multiple users, then the original change remains, and subsequent commits are blocked.
* If you try to commit a change that has been made already, you can merge those changes into your private configuration and then attempt to recommit.
* When the user issues a `rollback 0` command, only their changes are rolled back.

When users enter configuration mode with the `configure exclusive` command they have the following access:

* The user locks the configuration and prevents other users from making changes.
* Only the user that locked the configuration can make commits

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
