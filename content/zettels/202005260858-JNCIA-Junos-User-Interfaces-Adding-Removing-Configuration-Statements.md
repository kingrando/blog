---
title: "JNCIA-Junos | User Interfaces: Adding Removing Configuration Statements"
date: 2020-05-26T08:58:22-05:00
draft: false
zettel: true
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id: 14
---
## Notes
Configuration statements are the actual contents of the configuration files. An example is:

```nix
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

## Links
  * [JNCIA-Junos | Junos Fundamentals: Software Architecture](202005251440-JNCIA-Junos-Junos-Software-Architecture.md)
  * [JNCIA-Junos | Junos Fundamentals: Control and Forwarding Planes](202005251450-JNCIA-Junos-Junos-Fundamentals-Control-and-Forwarding-Planes.md)
  * [JNCIA-Junos | Junos Fundamentals: Transit and Exception Traffic](202005251905-JNCIA-Junos-Junos-Fundamentals-Transit-and-Exception-Traffic.md)
  * [JNCIA-Junos | User Interfaces: CLI Modes](202005251910-JNCIA-Junos-User-Interfaces-CLI-Modes.md)
  * [JNCIA-Junos | User Interfaces: CLI Help](202005251940-JNCIA-Junos-User-Interfaces-CLI-Help.md)
  * [JNCIA-Junos | User Interfaces: CLI Navigation](202005251955-JNCIA-Junos-User-Interfaces-CLI-Navigation.md)
  * [JNCIA-Junos | User Interfaces: CLI Filtering Output](202005252000-JNCIA-Junos-User-Interfaces-CLI-Filtering-Output.md)
  * [JNCIA-Junos | User Interfaces: Active versus Candidate Configuration](202005260819-JNCIA-Junos-User-Interfaces-Active-Versus-Candidate-Configuration.md)
  * [JNCIA-Junos | User Interfaces: Reverting to Previous Configuration](202005260853-JNCIA-Junos-User-Interfaces-Reverting-to-Previous-Configuration.md)
  * [JNCIA-Junos | User Interfaces: The J-Web Interface](202005260903-JNCIA-Junos-User-Interfaces-J-Web-Interface.md)
  * [JNCIA-Junos | Configuration Basics: Factory Default State](202005260925-JNCIA-Junos-Configuration-Basics-Factory-Default-State.md)