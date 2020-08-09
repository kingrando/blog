---
title: "JNCIA Junos | Configuration Basics: NTP and SNMP"
date: 2020-06-05T18:32:05-05:00
draft: false
type: "zettel"
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id:
  - "2"
---
## NTP
NTP on Junos:
  * Devices can provide a primary time reference. 
  * Supports client, server, and symmetric active modes
  * MD5 authentication support
  * If clocks are more than 1000 seconds, they are not synchronized

### Configuration
  * Set the NTP Boot server
    * `set system ntp boot-server ip-address`
  * Set the NTP server
    * `set system ntp server ip-address`
  * Set NTP authentication
    * `set system ntp authentication-key number type [md5 | sha1 | sha256] value key`

### Verification
  * Show system time
    * `show system uptime `
  * Show NTP servers
    * `show ntp associations `
	* Show NTP status of the device
    * `show ntp status   `

## SNMP
SNMP on Junos supports v1, 2c, and 3.

### Configuration
  * Set SNMP community string
    * `set snmp community community-name authorization [read-only | read-write]`
  * Set the IP addresses of clients that can use the community
    * `set snmp community community-name clients network/network-mask`
  * Create a client list with a set of IP addresses that can use the SNMP community.
    * `set snmp client-list list-name network/network-mask`
    * `set snmp community-name client-list-name list`
  * Configure SNMP Trap group name, port, and destination
    * `set snmp trap-group group-name destination-port port targets ip-address`

### Verification
  * Show SNMP configuration
    * `show configuration snmp`

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
