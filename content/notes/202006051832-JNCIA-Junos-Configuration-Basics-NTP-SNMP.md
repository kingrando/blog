---
title: "JNCIA Junos | Configuration Basics: NTP and SNMP"
date: 2020-06-05T18:32:05-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## NTP

NTP on Junos:

* Devices can provide a primary time reference
* Supports client, server, and symmetric active modes
* MD5 authentication support
* If clocks are more than 1000 seconds, they are not synchronized

### NTP Configuration

* Set the NTP Boot server

  ```bash
  # Command
  set system ntp boot-server <ip-address>
  # Example
  set system ntp boot-server 10.0.0.1
  ```

* Set the NTP server

  ```bash
  # Command
  set system ntp server <ip-address>
  # Example
  set system ntp server 10.0.0.1
  ```

* Set NTP authentication

  ```bash
  # Command
  set system ntp authentication-key <number> type [md5 | sha1 | sha256] value <key>
  # Example
  set system ntp authentication-key 1 type sha256 value ThisIsASecret
  ```

### NTP Verification

* Show system time

  ```bash
  # Command
  show system uptime
  # Output
  Current time: 2020-08-21 18:03:41 CDT
  Time Source:  LOCAL CLOCK
  System booted: 2020-05-15 14:44:22 CDT (14w0d 03:19 ago)
  Protocols started: 2020-05-15 14:56:08 CDT (14w0d 03:07 ago)
  Last configured: 2020-08-21 17:05:53 CDT (00:57:48 ago) by kameron
  6:03PM  up 98 days,  3:19, 2 users, load averages: 0.39, 0.51, 0.56
  ```

* Show NTP servers

  ```bash
  # Command
  show ntp association
  # Output
    remote         refid           st t when poll reach   delay   offset  jitter
  ===============================================================================
  10.0.0.1         .INIT.          16 -    -   64    0    0.000    0.000 4000.00
  ```

* Show NTP status of the device

  ```bash
  # Command
  show ntp status
  # Output
  status=c011 sync_alarm, sync_unspec, 1 event, event_restart,
  version="ntpd 4.2.0-a Thu Jun 28 03:52:42  2018 (1)", processor="amd64",
  system="FreeBSDJNPR-11.0-20180614.6c3f819_buil", leap=11, stratum=16,
  precision=-22, rootdelay=0.000, rootdispersion=0.105, peer=0,
  refid=INIT, reftime=00000000.00000000  Thu, Feb  7 2036  0:28:16.000,
  poll=4, clock=e2ead195.749b66c9  Fri, Aug 21 2020 18:04:53.455, state=0,
  offset=0.000, frequency=0.000, jitter=0.000, stability=0.000
  ```

## SNMP

SNMP on Junos supports v1, 2c, and 3.

### SNMP Configuration

* Set SNMP community string

  ```bash
  # Command
  set snmp community <community-name> authorization [read-only | read-write]
  # Example
  set snmp community SecretWord authorization read-only
  ```

* Set the IP addresses of clients that can use the community

  ```bash
  # Command
  set snmp community <community-name> clients <network/network-mask>
  # Example
  set snmp community SecretWord clients 10.0.0.0/24
  ```

* Create a client list with a set of IP addresses that can use the SNMP community.

  ```bash
  # Command
  set snmp client-list <list-name> <network/network-mask>
  set snmp community <community-name> client-list-name <list>
  # Example
  set snmp client-list MySNMPClients 10.0.0.0/24
  set snmp community SecretWord client-list-name MySNMPClients
  ```

* Configure SNMP Trap group name, port, and destination

  ```bash
  # Command
  set snmp trap-group <group-name> destination-port <port> targets <ip-address>
  # Example
  set snmp trap-group MyGroup destination-port 100 targets 10.0.0.1
  ```

### SNMP Verification

* Show SNMP configuration

  ```bash
  # Command
  show configuration snmp
  # Output
  [edit]
  kameron@RE4# show snmp
  client-list MySNMPClients {
      10.0.0.0/24;
  }
  community public {
      authorization read-only;
  }
  community SecretWord {
      authorization read-only;
      client-list-name MySNMPClients;
  }
  ```

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
