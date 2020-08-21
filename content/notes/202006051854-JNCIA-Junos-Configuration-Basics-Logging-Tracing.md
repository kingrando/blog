---
title: "JNCIA Junos | Configuration Basics: Logging and Tracing"
date: 2020-06-05T18:54:10-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Logging

Syslog files are stored in `/var/log/`. The primary syslog file is located at `/var/log/messages`.

* General syslog configuration options
  * `host name` or `ip-address`: Sends syslog messages to a remote host
  * `archive`: Configures how to archive system logging files (default is to keep 10 archive files with a maximum size of 128 K each)
  * `console`: Configures the types of syslog messages to log to the system console
  * `facility`: Displays the class of log messages
  * `severity`: Displays the severity level of log messages
  * `file filename`: Configures the name of the log file
  * `files number`: Displays the maximum number of system log files

### Logging Configuration

* Configure the host, facility, and severity level

  ```bash
  # Command
  set system syslog host <ip-address> <facility> <severity>
  # Example
  set system syslog host 10.0.0.1 firewall alerts
  ```

* Specify a filename to capture logs (Optional)

  ```bash
  # Command
  set system syslog file <file-name> <facility> <severity>
  # Example
  set system syslog file my_firewall_alerts.log firewall alerts
  ```

* Specify the maximum size of the log file

  ```bash
  # Command
  set system syslog file <file-name> archive size <size>
  # Example
  set system syslog file my_firewall_alerts.log archive size 1000000
  ```

### Logging Verification

* Show configuration

  ```bash
  # Command
  [edit]
  show system syslog
  # Output
  kameron@RE4# show system syslog
  host 10.0.0.1 {
      firewall alert;
  }
  file my_firewall_alerts.log {
      firewall alert;
      archive size 1000000;
  }
  ```

* Check the messages code:

  ```bash
  # Command
  help syslog <message-code>
  # Example
  kameron@RE4> help syslog BOOTPD_ARG_ERR
  Name:          BOOTPD_ARG_ERR
  Message:       Ignoring unknown option -<option>
  Help:          Command-line option was invalid
  Description:   The indicated option was provided on the 'tnp.bootpd' command line and is invalid. The boot parameter process (tnp.bootpd) initialized but
                ignored the invalid option.
  Type:          Error: An error occurred
  Severity:      warning
  Facility:      ANY
  Action:        Remove the invalid option from the 'tnp.bootpd' command line.
  ```

## Tracing

Tracing is the Junos OS equivalent of debug for Cisco. It requires configuration to use and provides local and remote options.

Tracing files are written to `/var/log/filename` or to a remote syslog server.

You can trace individual interfaces and interface processes, but you cannot specify a trace file for this. The trace files go to the messages file. By default, `/var/log/dcd` is used for global interface tracing.

Junos OS supports remote tracing for the following processes:

* **chassisd** - Chassis-control process
* **eventd** - Event-processing process
* **cosd** - Class-of-Service process
* **spd** - Adaptive-services process

Global tracing options define tracing for all routing protocols and is configured at `[edit routing-options]`.

Protocol-specific tracing operations define tracing for a specific routing protocol. It is configured at the `[edit protocols]` hierarchy when configuring the individual routing protocol. Configuration here will override the equivalent commands at the global level.

Tracing operations within individual routing protocol entities provides granular tracing options for a protocol such as BGP peer-specific tracing operations.

Interface tracing operations defines tracing for individual router interfaces and for the interface process itself. Configured at the `[edit interfaces]` hierarchy

### Tracing Configuration

* Enable remote tracing

  ```bash
  # Command
  set system tracing destination-override syslog host <address>
  # Example
  set system tracing destination-override syslog host 10.0.0.1
  ```

To override the system-wide remote tracing configuration for a process include the no-remote-trace statement at the `[edit process-name traceoptions]` hierarchy. When no-remote-trace is enabled, the process does local tracing.

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
