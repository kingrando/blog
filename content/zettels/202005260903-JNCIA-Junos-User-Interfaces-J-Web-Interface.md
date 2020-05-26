---
title: "JNCIA-Junos | User Interfaces: J-Web Interface"
date: 2020-05-26T09:03:08-05:00
draft: false
zettel: true
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id: 15
---
## Notes
### J-Web Interface Dashboards
The J-Web interface is a web GUI used to configure and manage Junos OS devices over HTTP or HTTPS. It has 5 primary tabs which perform the following functions:

  * The Summary tab
    * Contains system information and system status
    * Provides information regarding ports, alarms, security events, and device utilization.
  * The Configure tab
    * Provides 4 ways to configure the Junos OS device:
      * A point-and-click web GUI
      * A graphical version of the CLI configuration and hierarchy
      * In the configuration text file
      * Uploading of a configuration file
  * The Monitor tab
    * Display the current system information and configuration such as routing tables, interfaces, etc…
  * The Reports tab
    * Generate reports
  * The Administration tab
    * Perform file system maintenance
    * Perform software upgrades
    * Monitor the device with tools such as ping and traceroute
		
### Basic Settings Configuration Page
When you first configure a Junos device via the J-Web interface you can configure the basic settings of a device via a Basic Settings wizard. This wizard can be accessed via **Configure > Device Settings > Basic Settings**

On the Basic Settings screen, you can configure the following information:

  * System Identity Details 
    * Hostname
    * Domain Name
    * Root Password
    * DNS Server
    * Domain Search
  * Date & Time Details
  * Management Access Configuration
    * IP Address of the Management Port
    * The Loopback IP address
    * Access methods that are enabled
    * Services that are enabled
    * Ports that allow access through HTTP or HTTPS
    * System APIs that are enabled
    * Adding and Removing of system certificates
  * Security Logging
  * SNMP

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
  * [JNCIA-Junos | User Interfaces: Adding and Removing Configuration Statements](202005260858-JNCIA-Junos-User-Interfaces-Adding-Removing-Configuration-Statements.md)
  * [JNCIA-Junos | Configuration Basics: Factory Default State](202005260925-JNCIA-Junos-Configuration-Basics-Factory-Default-State.md)