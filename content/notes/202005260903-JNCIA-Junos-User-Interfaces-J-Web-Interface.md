---
title: "JNCIA-Junos | User Interfaces: J-Web Interface"
date: 2020-05-26T09:03:08-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## J-Web Interface Dashboards
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
		
## Basic Settings Configuration Page
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