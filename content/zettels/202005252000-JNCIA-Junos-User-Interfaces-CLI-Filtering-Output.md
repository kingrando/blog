---
title: "JNCIA-Junos | User Interfaces: CLI Filtering Output"
date: 2020-05-25T20:00:22-05:00
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