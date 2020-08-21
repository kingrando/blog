---
title: "JNCIA-Junos | User Interfaces: CLI Filtering Output"
date: 2020-05-25T20:00:22-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## How to Filter CLI Output

The command-line output for Junos OS commands can be modified and filtered using the pipe-key ( | ) along with modifiers.

The following are some of the modifiers available:

* `append` - Append output text to a file

    ```bash
    kameron@RE4> show interfaces | append /var/tmp/interfaces.log
    Wrote 740 lines of output to '/var/tmp/interfaces.log'
    ```

* `compare` - compare configuration changes with another file

    ```bash
    kameron@RE4# show | compare
    [edit system]
    -  host-name RE4;
    +  host-name Test;
    ```

* `count` - Count occurrences

    ```bash
    kameron@RE4> show interfaces | match Ethernet | count
    Count: 36 lines
    ```

* `display` - Show additional kinds of information

    ```bash
    kameron@RE4> show configuration | display set
    set version 18.2R1.9
    set groups baseline system login class admin idle-timeout 30
    ```

* `except` - Show only text that does not match a pattern

    ```bash
    kameron@RE4> show configuration | except interfaces
    ```

* `find` - Search for first occurrence of pattern

    ```bash
    kameron@RE4> show interfaces | find Ethernet
      Link-level type: Ethernet, MTU: 1518, MRU: 1526, LAN-PHY mode, Speed: 1000mbps, BPDU Error: None, Loop Detect PDU Error: None,
    ```

* `hold` - Hold text without exiting the --More-- prompt

    ```bash
    kameron@RE4> show configuration | hold
    ```

* `last` - Display end of output only

    ```bash
    kameron@RE4> show log messages | last
    ```

* `match` - Show only text that matches a pattern

    ```bash
    kameron@RE4> show interfaces | match Ethernet
    Link-level type: Ethernet, MTU: 1518, MRU: 1526, LAN-PHY mode, Speed: 1000mbps, BPDU Error: None, Loop Detect PDU Error: None,
    Ethernet-Switching Error: None, MAC-REWRITE Error: None, Loopback: Disabled, Source filtering: Disabled, Flow control: Enabled, Auto-negotiation: Enabled,
    ```

* `no-more` - Don't paginate output

    ```bash
    kameron@RE4> show configuration | no-more
    ```

* `refresh` - Refresh a continuous display of the command

    ```bash
    kameron@RE4> show interfaces ge-0/0/1 | refresh
    ---(refreshed at 2020-08-21 16:47:13 CDT)---
    Physical interface: ge-0/0/1, Enabled, Physical link is Up
      Interface index: 149, SNMP ifIndex: 527
    ```

* `request` - Make system-level requests

    ```bash
    kameron@RE4> show configuration | request message all
    ```

* `save` - Save output to a text-file

    ```bash
    kameron@RE4> show interfaces terse | save /var/tmp/interfaces.log
    Wrote 68 lines of output to '/var/tmp/interfaces.log'
    ```

* `tee` - Write to standard output and file

    ```bash
    kameron@RE4> show lldp neighbors | tee /var/tmp/lldp.log
    Local Interface    Parent Interface    Chassis Id          Port info          System Name
    ge-0/0/0           -                   2c:6b:f5:78:fe:c0   526                RE5
    ge-0/0/1           -                   2c:6b:f5:b5:33:c0   527                RE2

    kameron@RE4> file show /var/tmp/lldp.log
    Local Interface    Parent Interface    Chassis Id          Port info          System Name
    ge-0/0/0           -                   2c:6b:f5:78:fe:c0   526                RE5
    ge-0/0/1           -                   2c:6b:f5:b5:33:c0   527                RE2

    ```

* `trim` - trim specified number of columns from start of line

    ```bash
    kameron@RE4> show lldp neighbors | trim 10
    rface    Parent Interface    Chassis Id          Port info          System Name
            -                   2c:6b:f5:78:fe:c0   526                RE5
            -                   2c:6b:f5:b5:33:c0   527                RE2
    ```

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
