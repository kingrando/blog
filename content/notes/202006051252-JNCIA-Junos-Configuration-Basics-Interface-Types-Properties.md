---
title: "JNCIA Junos | Configuration Basics: Interface Types & Properties"
date: 2020-06-05T12:52:30-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Interface Types

There are 5 primary interface types on Junos devices:

* Management
  * Used to connect the device to an out of band (OOB) management network.
  * The naming of these interfaces is platform-specific, but examples include `fxp0` and `me0`.
* Internal
  * Used to connect the control plane and the forwarding plane together.
  * The naming of these interfaces is platform-specific, but examples include `fxp1` and `em0`.
* Network
  * Used to provide media connectivity.
  * Examples include `ae` (Aggregated Ethernet), `fe` (Fast Ethernet), `ge` (Gigabit Ethernet), and `xe` (10G ethernet).
* Services
  * Provide user-configurable services that are used to manipulate traffic before being delivered to the destination.
  * Services can be provided either through Physical Interface Cards (PICs) or through software.
  * Examples include `es` (encryption), `gr` (GRE tunnel), `ip` (IP-over-IP encapsulation), and `mo` (passive monitoring interface).
* Loopback
  * Provides a hardware independent interface.
  * Uses the `lo0` destination on all platforms.

### Interface Naming

Interface naming typically follows the convention of:

* `(Interface Media Type)-(Line Card Slot Number)/(Interface Slot Card Number)/(Port Number)`

Examples:

* `ge-0/0/1`
* `xe-1/1/1`

## Logical Units

Juniper interfaces can be subdivided from a single physical interface into multiple logical interfaces. This is a similar concept to Cisco's sub-interfaces. The difference is that all Juniper interfaces **must** have a logical unit number. This number is typically 0.

Encapsulation methods such as PPP and Cisco HDLC only support one logical interface and it **must** be 0.

Other encapsulation methods such as Frame Relay, ATM, and 802.1Q support multiple logical units.

**Note**: Logical unit numbers are separate in meaning from circuit identifiers and do not need to match. It is suggested to keep them the same though to aid in troubleshooting.

## Multiple Addresses

There is no limit on the number of IP addresses you can have on an interface.

By default, when you attempt to change an IP address on a Juniper device it will add an additional IP address to that interface instead of changing it. This is done with the following command:

* `set interfaces <interface-name> unit <unit number> family inet address <ip-address/mask>`

To change the IP address on an interface you must use the rename command and not the set command as shown:

* `rename interfaces <interface-name> unit <unit number> family inet address <ip-address/mask> to address <ip-address/mask>`

## Interface Properties

There are two types of interface properties: *physical* and *logical*.

The *Physical Interface* properties are those that define physical characteristics about the interface such as:

* Data Link Layer protocol and keepalives
* **Link Mode**: Full or Half-duplex
* Speed
* MTU
* **Clocking**: Internal or External
* **Scrambling**: Payload scrambling
* **Frame Check Sequence (FCS)**: Default is 16-bit but can be 32-bit
* **Diagnostic characteristics**: Enable local or remote loopbacks or setup a bit error rate test (BERT)

The *Logical Interface* properties are those that describe the more abstract items such as:

* **Protocol family**: inet, inet6, iso, mpls, or bridge
* Addresses
* **Virtual circuits**: Data-Link Connection Identifier (DLCI), Virtual Path Identifier (VPI), Virtual Channel Identifier (VCI), or VLAN tag
* **Other characteristics**: Inverse ARP, traps, accounting profiles

## Interface Configuration

* Create an interface:

    ```bash
    # Command
    set interfaces <interface-name> unit <unit-number>
    # Example
    set interfaces ge-0/0/0 unit 0
    ```

* Assign an IP address

    ```bash
    # Command
    set interfaces <interface-name> unit <unit-number> family inet address <ip-address/prefix-length>
    # Example
    set interfaces ge-0/0/0 unit 0 family inet address 10.0.0.1/24
    ```

* Set a description

    ```bash
    # Command
    set interfaces <interface-name> unit <unit-number> description <description>
    # Example
    set interfaces ge-0/0/0 unit 0 description "This is a description"
    ```

* Set VLAN ID

    ```bash
    # Command
    set interfaces <interface-name> unit <unit-number> vlan-id <vlan-id>
    # Example
    set interfaces ge-0/0/0 unit 0 vlan-id 10
    ```

## Interface Verification

* Show operational information regarding interface:
  * **Note**: If ran in configuration mode, it will display the configuration of that interface.

  ```bash
  # Command
  show interfaces
  # Output
  Physical interface: ge-0/0/0, Enabled, Physical link is Up
  Interface index: 148, SNMP ifIndex: 526
  Link-level type: Ethernet, MTU: 1518, MRU: 1526, LAN-PHY mode, Speed: 1000mbps, BPDU Error: None, Loop Detect PDU Error: None,
  Ethernet-Switching Error: None, MAC-REWRITE Error: None, Loopback: Disabled, Source filtering: Disabled, Flow control: Enabled, Auto-negotiation: Enabled,
  Remote fault: Online
  Pad to minimum frame size: Disabled
  Device flags   : Present Running
  Interface flags: SNMP-Traps Internal: 0x4000
  CoS queues     : 8 supported, 8 maximum usable queues
  Current address: 50:00:00:05:00:02, Hardware address: 50:00:00:05:00:02
  Last flapped   : 2020-07-27 17:54:29 CDT (3w3d 23:55 ago)
  Input rate     : 0 bps (0 pps)
  Output rate    : 0 bps (0 pps)
  Active alarms  : None
  Active defects : None
  PCS statistics                      Seconds
    Bit errors                             0
    Errored blocks                         0
  Ethernet FEC statistics              Errors
    FEC Corrected Errors                    0
    FEC Uncorrected Errors                  0
    FEC Corrected Errors Rate               0
    FEC Uncorrected Errors Rate             0
  Interface transmit statistics: Disabled

  Logical interface ge-0/0/0.0 (Index 336) (SNMP ifIndex 536)
    Description: TO-R5
    Flags: Up SNMP-Traps 0x4000 VLAN-Tag [ 0x8100.1 ]  Encapsulation: ENET2
    Input packets : 117071
    Output packets: 117354
    Protocol inet, MTU: 1500
    Max nh cache: 75000, New hold nh limit: 75000, Curr nh cnt: 1, Curr new hold cnt: 0, NH drop cnt: 0
      Flags: Sendbcast-pkt-to-re
      Addresses, Flags: Is-Preferred Is-Primary
        Destination: 10.0.4.0/30, Local: 10.0.4.1, Broadcast: 10.0.4.3
    Protocol multiservice, MTU: Unlimited
      Flags: Is-Primary
    ```
  
* Show an abbreviated list of interfaces including admin, link-state status, protocol, and IP address.
  
    ```bash
    # Command
    show interfaces terse
    # Output
    Interface               Admin Link Proto    Local                 Remote
    ge-0/0/0                up    up
    ge-0/0/0.0              up    up   inet     10.0.4.1/30
                                      multiservice
    ge-0/0/0.1              up    up   inet     172.16.10.2/30
                                      multiservice
    ge-0/0/0.32767          up    up   multiservice
    lc-0/0/0                up    up
    ```

* Show detailed information about an interface including status, physical characteristics, and traffic counters.

  ```bash
  # Command
  show interfaces detail
  # Output
  Physical interface: ge-0/0/1, Enabled, Physical link is Up
  Interface index: 149, SNMP ifIndex: 527, Generation: 204
  Link-level type: Ethernet, MTU: 1518, MRU: 1526, LAN-PHY mode, Speed: 1000mbps, BPDU Error: None, Loop Detect PDU Error: None,
  Ethernet-Switching Error: None, MAC-REWRITE Error: None, Loopback: Disabled, Source filtering: Disabled, Flow control: Enabled, Auto-negotiation: Enabled,
  Remote fault: Online
  Pad to minimum frame size: Disabled
  Device flags   : Present Running
  Interface flags: SNMP-Traps Internal: 0x4000
  CoS queues     : 8 supported, 8 maximum usable queues
  Hold-times     : Up 0 ms, Down 0 ms
  Damping        : half-life: 0 sec, max-suppress: 0 sec, reuse: 0, suppress: 0, state: unsuppressed
  Current address: 50:00:00:05:00:03, Hardware address: 50:00:00:05:00:03
  Last flapped   : 2020-08-21 17:05:54 CDT (00:46:10 ago)
  Statistics last cleared: Never
  Traffic statistics:
   Input  bytes  :             52842492                  312 bps
   Output bytes  :             61652975                    0 bps
   Input  packets:               454278                    0 pps
   Output packets:               454958                    0 pps
   IPv6 transit statistics:
   Input  bytes  :                    0
   Output bytes  :                    0
   Input  packets:                    0
   Output packets:                    0
  Active alarms  : None
  Active defects : None
  PCS statistics                      Seconds
    Bit errors                             0
    Errored blocks                         0
  Ethernet FEC statistics              Errors
    FEC Corrected Errors                    0
    FEC Uncorrected Errors                  0
    FEC Corrected Errors Rate               0
    FEC Uncorrected Errors Rate             0
  Interface transmit statistics: Disabled

  Logical interface ge-0/0/1.0 (Index 339) (SNMP ifIndex 537) (Generation 177)
    Description: TO-R2
    Flags: Up SNMP-Traps 0x4000 VLAN-Tag [ 0x8100.1 ]  Encapsulation: ENET2
    Traffic statistics:
     Input  bytes  :                28064
     Output bytes  :                33758
     Input  packets:                  350
     Output packets:                  347
    Local statistics:
     Input  bytes  :                27984
     Output bytes  :                33758
     Input  packets:                  349
     Output packets:                  347
    Transit statistics:
     Input  bytes  :                   80                    0 bps
     Output bytes  :                    0                    0 bps
     Input  packets:                    1                    0 pps
     Output packets:                    0                    0 pps
    Protocol inet, MTU: 1500
    Max nh cache: 75000, New hold nh limit: 75000, Curr nh cnt: 1, Curr new hold cnt: 0, NH drop cnt: 0
    Generation: 215, Route table: 0
      Flags: Sendbcast-pkt-to-re
      Addresses, Flags: Is-Preferred Is-Primary
        Destination: 10.0.3.0/30, Local: 10.0.3.2, Broadcast: 10.0.3.3, Generation: 176
    Protocol multiservice, MTU: Unlimited, Generation: 216, Route table: 0
      Policer: Input: __default_arp_policer__

  Logical interface ge-0/0/1.1 (Index 333) (SNMP ifIndex 540) (Generation 175)
    Flags: Up SNMP-Traps 0x4000 VLAN-Tag [ 0x8100.100 ]  Encapsulation: ENET2
    Traffic statistics:
     Input  bytes  :                29016
     Output bytes  :                35024
     Input  packets:                  365
     Output packets:                  364
    Local statistics:
     Input  bytes  :                28940
     Output bytes  :                35024
     Input  packets:                  364
     Output packets:                  364
    Transit statistics:
     Input  bytes  :                   76                    0 bps
     Output bytes  :                    0                    0 bps
     Input  packets:                    1                    0 pps
     Output packets:                    0                    0 pps
    Protocol inet, MTU: 1500
    Max nh cache: 75000, New hold nh limit: 75000, Curr nh cnt: 1, Curr new hold cnt: 0, NH drop cnt: 0
    Generation: 212, Route table: 8
      Flags: Sendbcast-pkt-to-re
      Addresses, Flags: Is-Preferred Is-Primary
        Destination: 172.16.10.8/30, Local: 172.16.10.10, Broadcast: 172.16.10.11, Generation: 174
    Protocol multiservice, MTU: Unlimited, Generation: 213, Route table: 8
      Policer: Input: __default_arp_policer__

  Logical interface ge-0/0/1.32767 (Index 334) (SNMP ifIndex 541) (Generation 176)
    Flags: Up SNMP-Traps 0x4004000 VLAN-Tag [ 0x0000.0 ]  Encapsulation: ENET2
    Traffic statistics:
     Input  bytes  :                32239
     Output bytes  :                39463
     Input  packets:                  103
     Output packets:                  106
    Local statistics:
     Input  bytes  :                32239
     Output bytes  :                39463
     Input  packets:                  103
     Output packets:                  106
    Transit statistics:
     Input  bytes  :                    0                    0 bps
     Output bytes  :                    0                    0 bps
     Input  packets:                    0                    0 pps
     Output packets:                    0                    0 pps
    Protocol multiservice, MTU: Unlimited, Generation: 214, Route table: 0
      Flags: None
      Policer: Input: __default_arp_policer__
    ```

* Show extensive information about an interface including output from `show interfaces detail` plus error counters.

    ```bash
    # Command
    show interfaces extensive
    # Output
    Physical interface: ge-0/0/1, Enabled, Physical link is Up
      Interface index: 149, SNMP ifIndex: 527, Generation: 204
      Link-level type: Ethernet, MTU: 1518, MRU: 1526, LAN-PHY mode, Speed: 1000mbps, BPDU Error: None, Loop Detect PDU Error: None,
      Ethernet-Switching Error: None, MAC-REWRITE Error: None, Loopback: Disabled, Source filtering: Disabled, Flow control: Enabled, Auto-negotiation: Enabled,
      Remote fault: Online
      Pad to minimum frame size: Disabled
      Device flags   : Present Running
      Interface flags: SNMP-Traps Internal: 0x4000
      CoS queues     : 8 supported, 8 maximum usable queues
      Hold-times     : Up 0 ms, Down 0 ms
      Damping        : half-life: 0 sec, max-suppress: 0 sec, reuse: 0, suppress: 0, state: unsuppressed
      Current address: 50:00:00:05:00:03, Hardware address: 50:00:00:05:00:03
      Last flapped   : 2020-08-21 17:05:54 CDT (00:46:57 ago)
      Statistics last cleared: Never
      Traffic statistics:
      Input  bytes  :             52844078                  224 bps
      Output bytes  :             61654653                  408 bps
      Input  packets:               454292                    0 pps
      Output packets:               454970                    0 pps
      IPv6 transit statistics:
      Input  bytes  :                    0
      Output bytes  :                    0
      Input  packets:                    0
      Output packets:                    0
      Dropped traffic statistics due to STP State:
      Input  bytes  :                    0
      Output bytes  :                    0
      Input  packets:                    0
      Output packets:                    0
      Input errors:
        Errors: 0, Drops: 0, Framing errors: 0, Runts: 0, Policed discards: 0, L3 incompletes: 0, L2 channel errors: 0, L2 mismatch timeouts: 0, FIFO errors: 0,
        Resource errors: 0
      Output errors:
        Carrier transitions: 3, Errors: 0, Drops: 0, Collisions: 0, Aged packets: 0, FIFO errors: 0, HS link CRC errors: 0, MTU errors: 0, Resource errors: 0
      Active alarms  : None
      Active defects : None
      PCS statistics                      Seconds
        Bit errors                             0
        Errored blocks                         0
      Ethernet FEC statistics              Errors
        FEC Corrected Errors                    0
        FEC Uncorrected Errors                  0
        FEC Corrected Errors Rate               0
        FEC Uncorrected Errors Rate             0
      MAC statistics:                      Receive         Transmit
        Total octets                      58911348         64383576
        Total packets                       454413           454962
        Unicast packets                     454413           454961
        Broadcast packets                        0                0
        Multicast packets                        0                0
        CRC/Align errors                         0                0
        FIFO errors                              0                0
        MAC control frames                       0                0
        MAC pause frames                         0                0
        Oversized frames                         0
        Jabber frames                            0
        Fragment frames                          0
        VLAN tagged frames                       0
        Code violations                          0
        Total errors                             0                0
      Filter statistics:
        Input packet count                  454403
        Input packet rejects                    57
        Input DA rejects                         0
        Input SA rejects                         0
        Output packet count                                  454951
        Output packet pad count                                   0
        Output packet error count                                 0
        CAM destination filters: 0, CAM source filters: 0
      Autonegotiation information:
        Negotiation status: Incomplete
      Packet Forwarding Engine configuration:
        Destination slot: 0 (0x00)
      CoS information:
        Direction : Output
        CoS transmit queue               Bandwidth               Buffer Priority   Limit
                                  %            bps     %           usec
        0 best-effort            95      950000000    95              0      low    none
        3 network-control         5       50000000     5              0      low    none
      Interface transmit statistics: Disabled

      Logical interface ge-0/0/1.0 (Index 339) (SNMP ifIndex 537) (Generation 177)
        Description: TO-R2
        Flags: Up SNMP-Traps 0x4000 VLAN-Tag [ 0x8100.1 ]  Encapsulation: ENET2
        Traffic statistics:
        Input  bytes  :                28464
        Output bytes  :                34248
        Input  packets:                  355
        Output packets:                  352
        Local statistics:
        Input  bytes  :                28384
        Output bytes  :                34248
        Input  packets:                  354
        Output packets:                  352
        Transit statistics:
        Input  bytes  :                   80                    0 bps
        Output bytes  :                    0                    0 bps
        Input  packets:                    1                    0 pps
        Output packets:                    0                    0 pps
        Protocol inet, MTU: 1500
        Max nh cache: 75000, New hold nh limit: 75000, Curr nh cnt: 1, Curr new hold cnt: 0, NH drop cnt: 0
        Generation: 215, Route table: 0
          Flags: Sendbcast-pkt-to-re
          Addresses, Flags: Is-Preferred Is-Primary
            Destination: 10.0.3.0/30, Local: 10.0.3.2, Broadcast: 10.0.3.3, Generation: 176
        Protocol multiservice, MTU: Unlimited, Generation: 216, Route table: 0
          Policer: Input: __default_arp_policer__

      Logical interface ge-0/0/1.1 (Index 333) (SNMP ifIndex 540) (Generation 175)
        Flags: Up SNMP-Traps 0x4000 VLAN-Tag [ 0x8100.100 ]  Encapsulation: ENET2
        Traffic statistics:
        Input  bytes  :                29656
        Output bytes  :                35612
        Input  packets:                  373
        Output packets:                  370
        Local statistics:
        Input  bytes  :                29500
        Output bytes  :                35612
        Input  packets:                  371
        Output packets:                  370
        Transit statistics:
        Input  bytes  :                  156                   64 bps
        Output bytes  :                    0                    0 bps
        Input  packets:                    2                    0 pps
        Output packets:                    0                    0 pps
        Protocol inet, MTU: 1500
        Max nh cache: 75000, New hold nh limit: 75000, Curr nh cnt: 1, Curr new hold cnt: 0, NH drop cnt: 0
        Generation: 212, Route table: 8
          Flags: Sendbcast-pkt-to-re
          Addresses, Flags: Is-Preferred Is-Primary
            Destination: 172.16.10.8/30, Local: 172.16.10.10, Broadcast: 172.16.10.11, Generation: 174
        Protocol multiservice, MTU: Unlimited, Generation: 213, Route table: 8
          Policer: Input: __default_arp_policer__

      Logical interface ge-0/0/1.32767 (Index 334) (SNMP ifIndex 541) (Generation 176)
        Flags: Up SNMP-Traps 0x4004000 VLAN-Tag [ 0x0000.0 ]  Encapsulation: ENET2
        Traffic statistics:
        Input  bytes  :                33178
        Output bytes  :                40209
        Input  packets:                  106
        Output packets:                  108
        Local statistics:
        Input  bytes  :                33178
        Output bytes  :                40209
        Input  packets:                  106
        Output packets:                  108
        Transit statistics:
        Input  bytes  :                    0                    0 bps
        Output bytes  :                    0                    0 bps
        Input  packets:                    0                    0 pps
        Output packets:                    0                    0 pps
        Protocol multiservice, MTU: Unlimited, Generation: 214, Route table: 0
          Flags: None
          Policer: Input: __default_arp_policer__
    ```

* Show descriptions for interfaces
  
    ```bash
    # Command
    show interfaces description
    # Output
    Interface       Admin Link Description
    ge-0/0/0.0      up    up   TO-R5
    ge-0/0/1.0      up    up   TO-R2
    ```

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
