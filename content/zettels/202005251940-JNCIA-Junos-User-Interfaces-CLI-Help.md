---
title: "JNCIA-Junos | User Interfaces: CLI Help"
date: 2020-05-25T19:40:51-05:00
draft: false
zettel: true
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id: 9
---
## Notes
Junos contains two types of help: Context-Sensitive help and Topical help. 

### Context-Sensitive Help
Used to get the list of commands, options, and user-defined variables that are available in a given context. This is obtained by typing a command out and following it with a ? mark. 

```nix
kameron@RE1> show configuration interfaces ge-0/0/?
Possible completions:
  <interface-name>     Interface name
  ge-0/0/0             Interface name
  ge-0/0/1             Interface name
  ge-0/0/2             Interface name
  ge-0/0/4             Interface name
```

### Topical Help
There are 3 types of topical help in Junos: topic, reference, and apropos

#### Help Topic
Displays usage guidelines for a command. 

```nix
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

#### Help Reference
Displays summary information for the referenced configuration statement.

```nix
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

#### Help Apropos
Displays contexts that reference a specific variable

```nix
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

## Links
  * [JNCIA-Junos | Junos Fundamentals: Software Architecture](202005251440-JNCIA-Junos-Junos-Software-Architecture.md)
  * [JNCIA-Junos | Junos Fundamentals: Control and Forwarding Planes](202005251450-JNCIA-Junos-Junos-Fundamentals-Control-and-Forwarding-Planes.md)
  * [JNCIA-Junos | Junos Fundamentals: Transit and Exception Traffic](202005251905-JNCIA-Junos-Junos-Fundamentals-Transit-and-Exception-Traffic.md)
  * [JNCIA-Junos | User Interfaces: CLI Modes](202005251910-JNCIA-Junos-User-Interfaces-CLI-Modes.md)
  * [JNCIA-Junos | User Interfaces: CLI Navigation](202005251955-JNCIA-Junos-User-Interfaces-CLI-Navigation.md)
  * [JNCIA-Junos | User Interfaces: CLI Filtering Output](202005252000-JNCIA-Junos-User-Interfaces-CLI-Filtering-Output.md)
  * [JNCIA-Junos | User Interfaces: Active versus Candidate Configuration](202005260819-JNCIA-Junos-User-Interfaces-Active-Versus-Candidate-Configuration.md)
  * [JNCIA-Junos | User Interfaces: Reverting to Previous Configuration](202005260853-JNCIA-Junos-User-Interfaces-Reverting-to-Previous-Configuration.md)
  * [JNCIA-Junos | User Interfaces: Adding and Removing Configuration Statements](202005260858-JNCIA-Junos-User-Interfaces-Adding-Removing-Configuration-Statements.md)
  * [JNCIA-Junos | User Interfaces: The J-Web Interface](202005260903-JNCIA-Junos-User-Interfaces-J-Web-Interface.md)
  * [JNCIA-Junos | Configuration Basics: Factory Default State](202005260925-JNCIA-Junos-Configuration-Basics-Factory-Default-State.md)