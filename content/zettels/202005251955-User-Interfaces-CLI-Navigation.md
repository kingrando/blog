---
title: "User Interfaces: CLI Navigation"
date: 2020-05-25T19:55:26-05:00
draft: false
zettel: true
tags:
  - JNCIA-Junos
  - Junos
  - Juniper
  - Networking
id: 10
---
## Notes
### Command Completion
Junos OS provides two ways to complete commands using the CLI. 

  1. Space Bar
    * For instance, typing set ch followed by spacebar will complete the command to set chassis. 
    * This can be disabled using the following command: `set cli complete-on-space off`
  2. Tab
     * Completes commands and variables such as policy names, AS paths, community names, and IP addresses.
     * For instance, if an interface has an IP address configured on it, the following command can be entered followed by tab: set interface ge-0/0/0 unit 0 family inet address 1 , followed by tab and it will complete to set interface ge-0/0/0 unit 0 family inet address 10.0.1.1/30 or whatever the IP address is set to.

### Editing Command Lines
The Junos OS uses a default VT100 terminal types for commands and arrow keys. The platform also supports emac commands for moving around the lines which include:

  * Ctrl+b - Left one character
  * Ctrl+a - Beginning of line
  * Ctrl+a - Right one character
  * Ctrl+e - End of line
  * Ctrl+d - Deletes the character over the cursor
  * Ctrl+k - Deletes from the cursor to the end of the line
  * Ctrl+u - Deletes all characters and negates the current command
  * Ctrl+w - Deletes the entire word to the left of the cursor
  * Ctrl+l - Redraws the current line
  * Ctrl+p - Repeats the previous command in the command history
  * Ctrl+n - Repeats the next command in the command history
  * Esc+d - Deletes the word to the right
  * Esc+b - Moves the cursor back one word with no delete
  * Esc+f - Moves the cursor forward one word with no delete

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)

## Links
  * [Junos OS Fundamentals: Software Architecture](202005201440-Junos-Software-Architecture.md)
  * [Junos Fundamentals: Control and Forwarding Planes](202005251450-Junos-Fundamentals-Control-and-Forwarding-Planes.md)
  * [Junos Fundamentals: Transit and Exception Traffic](202005251905-Junos-Fundamentals-Transit-and-Exception-Traffic.md)
  * [User Interfaces: CLI Modes](202005251910-User-Interfaces-CLI-Modes.md)
  * [User Interfaces: CLI Help](202005251940-User-Interfaces-CLI-Help.md)
  * [User Interfaces: CLI Filtering Output](202005252000-User-Interfaces-CLI-Filtering-Output.md)