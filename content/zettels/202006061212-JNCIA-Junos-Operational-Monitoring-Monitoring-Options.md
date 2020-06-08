---
title: "JNCIA Junos | Operational Monitoring and Maintenance: Monitoring Options"
date: 2020-06-06T12:12:41-05:00
draft: false
type: "zettel"
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id:
  - "3"
---
## Monitoring Options
Junos OS can be monitored by 6 different methods:

  1. Junos OS CLI
  2. Junos Space
  3. J-Web Interface
  4. SNMP
  5. LEDs
  6. LCDs

## Monitoring System Level Operations
System level operations can be monitored using the `show system` command hierarchy. The following common command combinations are available:

  * Display current system alarms
    * `show system alarms`
  * Display messages seen during the last boot
    * `show system boot-messages`
  * Display the status of local TCP and UDP sessions
    * `show system connections`
  * Display the model, device family, Junos version, and hostname.
    * `show system information`
  * Display the configuration for a specific rollback number
    * `show system rollback number`
  * Display various protocol statistics
    * `show system statistics`
  * Display the local storage information
    * `show system storage`

## Monitoring the Chassis
The chassis can be monitored using the `show chassis` command hierarchy. The following are some common command combinations:
  
  * Display current alarms about the chassis
    * `show chassis alarms`
  * Display component and environmental status as well as operational speeds of the cooling system
    * `show chassis environment`
  * Display active errors
    * `show chassis errors active`
  * Displays inventory of the installed hardware components along with serial numbers
    * `show chassis hardware`
  * Displays operational status and utilization details of the routing engines
    * `show chassis routing-engine`

## Monitoring Device Traffic
The following options can be used to monitor traffic and performance:

  * Start ethernet performance measurement
    * `monitor ethernet`
  * Show interface traffic
    * `monitor interface`
  * Show label-switched-path traffic
    * `monitor label-switched-path`
  * Show status of monitored files
    * `monitor list`
  * Monitor MPLS LSPs
    * `monitor mpls`
  * Start showing log file in real time
    * `monitor start `
  * Show static label-switched-path traffic
    * `monitor static-lsp`
  * Stop showing log file in real time
    * `monitor stop`
  * Show real-time network traffic information
    * `monitor traffic`

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)