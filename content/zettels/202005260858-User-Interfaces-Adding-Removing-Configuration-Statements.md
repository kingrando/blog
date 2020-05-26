---
title: "User Interfaces: Adding Removing Configuration Statements"
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
  * [Junos OS Fundamentals: Software Architecture](202005201440-Junos-Software-Architecture.md)
  * [Junos Fundamentals: Control and Forwarding Planes](202005251450-Junos-Fundamentals-Control-and-Forwarding-Planes.md)
  * [Junos Fundamentals: Transit and Exception Traffic](202005251905-Junos-Fundamentals-Transit-and-Exception-Traffic.md)
  * [User Interfaces: CLI Modes](202005251910-User-Interfaces-CLI-Modes.md)
  * [User Interfaces: CLI Help](202005251940-User-Interfaces-CLI-Help.md)
  * [User Interfaces: CLI Navigation](202005251955-User-Interfaces-CLI-Navigation.md)
  * [User Interfaces: CLI Filtering Output](202005252000-User-Interfaces-CLI-Filtering-Output.md)
  * [User Interfaces: Active versus Candidate Configuration](202005260819-User-Interfaces-Active-Versus-Candidate-Configuration.md)
  * [User Interfaces: Reverting to Previous Configuration](202005260853-User-Interfaces-Reverting-to-Previous-Configuration.md)
  * [User Interfaces: The J-Web Interface](202005260903-User-Interfaces-J-Web-Interface.md)
