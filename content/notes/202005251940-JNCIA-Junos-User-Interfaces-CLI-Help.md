---
title: "JNCIA-Junos | User Interfaces: CLI Help"
date: 2020-05-25T19:40:51-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Context-Sensitive Help
Used to get the list of commands, options, and user-defined variables that are available in a given context. This is obtained by typing a command out and following it with a ? mark. 

```bash
kameron@RE1> show configuration interfaces ge-0/0/?
Possible completions:
  <interface-name>     Interface name
  ge-0/0/0             Interface name
  ge-0/0/1             Interface name
  ge-0/0/2             Interface name
  ge-0/0/4             Interface name
```

## Topical Help
There are 3 types of topical help in Junos: topic, reference, and apropos

### Help Topic
Displays usage guidelines for a command. 

```bash
kameron@RE1> help topic system host-name
                Configuring the Hostname of the Router or Switch

   To configure the name of the router or switch, include the host-name
   statement at the [edit system] hierarchy level:
     [edit system]
         host-name hostname;
   The name value must be less than 256 characters.

  Related-Topics

        * Example: Configuring the Name of the Router, IP Address, and System
          ID
        * Example: Configuring the Name of the Switch, IP Address, and System
          ID
        * Configuring Basic Router or Switch Properties
        * Mapping the Hostname of the Switch to IP Addresses
        * host-name
```
### Help Reference
Displays summary information for the referenced configuration statement.

```bash
kameron@RE1> help reference system host-name
                                   host-name

    Syntax

   host-name hostname;

    Hierarchy Level

   [edit system]

    Release Information

   Statement introduced before JUNOS Release 7.4.

   Statement introduced in JUNOS Release 9.0 for EX Series switches.

    Description

   Set the hostname of the router or switch.

    Options

   hostname--Name of the router or switch.

    Required Privilege Level

   system--To view this statement in the configuration.

   system-control--To add this statement to the configuration.

    Related Topics

     * Configuring the Hostname of the Router
```

### Help Apropos
Displays contexts that reference a specific variable

```bash
kameron@RE1> help apropos system
monitor label-switched-path logical-system <logical-system>
    Name of logical system
monitor static-lsp logical-system <logical-system>
    Name of logical system
monitor ethernet delay-measurement logical-system <logical-system>
    Name of logical system
monitor ethernet synthetic-loss-measurement logical-system <logical-system>
    Name of logical system
restart routing logical-system <logical-system>
    Name of logical system
clear
    Clear information in the system
clear cli logical-system
    Clear logical system association
clear system
    Clear system information
clear system login
    Clear system login state
clear system errors
    Clear system errors
---(more---
```

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)