---
title: "User Interfaces: CLI Filtering Output"
date: 2020-05-25T20:00:22-05:00
draft: false
zettel: true
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id: 11
---
## Notes
Filtering Command-Line Output
The command-line output for Junos OS commands can be modified and filtered using the pipe-key ( | ) along with modifiers. 

The following are some of the modifiers available:

  * `append` - Append output text to a file
  * `compare` - compare configuration changes with another file
  * `count` - Count occurrences
  * `detail` - Display configuration data detail
  * `display` - Show additional kinds of information
  * `except` - Show only text that does not match a pattern
  * `find` - Search for first occurrence of pattern
  * `hold` - Hold text without exiting the --More-- prompt
  * `last` - Display end of output only
  * `match` - Show only text that matches a pattern
  * `no-more` - Don't paginate output
  * `refresh` - Refresh a continuous display of the command
  * `request` - Make system-level requests
  * `save` - Save output to a text-file
  * `tee` - Write to standard output and file
  * `trim` - trim specified number of columns from start of line

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)

## Links
  * [Junos OS Fundamentals: Software Architecture](202005201440-Junos-Software-Architecture.md)
  * [Junos Fundamentals: Control and Forwarding Planes](202005251450-Junos-Fundamentals-Control-and-Forwarding-Planes.md)
  * [Junos Fundamentals: Transit and Exception Traffic](202005251905-Junos-Fundamentals-Transit-and-Exception-Traffic.md)
  * [User Interfaces: CLI Modes](202005251910-User-Interfaces-CLI-Modes.md)
  * [User Interfaces: CLI Help](202005251940-User-Interfaces-CLI-Help.md)
  * [User Interfaces: CLI Navigation](202005251955-User-Interfaces-CLI-Navigation.md)
  * [User Interfaces: Active versus Candidate Configuration](202005260819-User-Interfaces-Active-Versus-Candidate-Configuration.md)
  * [User Interfaces: Reverting to Previous Configuration](202005260853-User-Interfaces-Reverting-to-Previous-Configuration.md)