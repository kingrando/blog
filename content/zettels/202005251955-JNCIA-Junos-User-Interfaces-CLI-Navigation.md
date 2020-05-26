---
title: "JNCIA-Junos | User Interfaces: CLI Navigation"
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
     * **Example**: typing set ch followed by spacebar will complete the command to set chassis. 
     * This can be disabled using the following command: `set cli complete-on-space off`
  1. Tab
     * Completes commands and variables such as policy names, AS paths, community names, and IP addresses.
     * **Example**: if an interface has an IP address configured on it, the following command can be entered followed by tab: set interface ge-0/0/0 unit 0 family inet address 1 , followed by tab and it will complete to set interface ge-0/0/0 unit 0 family inet address 10.0.1.1/30 or whatever the IP address is set to.

### Editing Command Lines
The Junos OS uses a default VT100 terminal types for commands and arrow keys. The platform also supports emac commands for moving around the lines which include:

  * `Ctrl+b` - Left one character
  * `Ctrl+a` - Beginning of line
  * `Ctrl+a` - Right one character
  * `Ctrl+e` - End of line
  * `Ctrl+d` - Deletes the character over the cursor
  * `Ctrl+k` - Deletes from the cursor to the end of the line
  * `Ctrl+u`- Deletes all characters and negates the current command
  * `Ctrl+w` - Deletes the entire word to the left of the cursor
  * `Ctrl+l` - Redraws the current line
  * `Ctrl+p` - Repeats the previous command in the command history
  * `Ctrl+n` - Repeats the next command in the command history
  * `Esc+d` - Deletes the word to the right
  * `Esc+b` - Moves the cursor back one word with no delete
  * `Esc+f` - Moves the cursor forward one word with no delete

### Moving Between Levels
Since the Junos OS is a hierarchy configuration, you are able to move between the hierarchy levels. The following options are available to move between levels:

  * `edit` - Used to specify your desired hierarchy level. 
    * **Example**: edit interfaces ge-0/0/0.0 
  * `up` - Moves you up one level in the configuration. 
    * **Example**: if you are at `[edit interfaces ge-0/0/0 unit 0]` and we issue the up command, it will take us to `[edit interfaces ge-0/0/0]`
  * `up n` - Moves you up the number placed at n. 
    * **Example**: if you are at `[edit interfaces ge-0/0/0 unit 0]` and we issue the command up 3, it will take us to `[edit]` 
  * `top` - Moves to the top of the configuration hierarchy. 
    * **Example**: if we are at `[edit interfaces ge-0/0/0 unit 0 family inet]` and we issue the command top, it will take us to `[edit]`
  * `exit` - Returns the user to the most recent, higher level hierarchy. 
    * **Example**: if we are at `[edit interfaces ge-0/0/0 unit 0]` and we navigate to `[edit family inet]` and then issue the exit command, it will take us to `[edit interfaces ge-0/0/0 unit 0]`

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)

## Links
  * [JNCIA-Junos | Junos Fundamentals: Software Architecture](202005251440-JNCIA-Junos-Junos-Software-Architecture.md)
  * [JNCIA-Junos | Junos Fundamentals: Control and Forwarding Planes](202005251450-JNCIA-Junos-Junos-Fundamentals-Control-and-Forwarding-Planes.md)
  * [JNCIA-Junos | Junos Fundamentals: Transit and Exception Traffic](202005251905-JNCIA-Junos-Junos-Fundamentals-Transit-and-Exception-Traffic.md)
  * [JNCIA-Junos | User Interfaces: CLI Modes](202005251910-JNCIA-Junos-User-Interfaces-CLI-Modes.md)
  * [JNCIA-Junos | User Interfaces: CLI Help](202005251940-JNCIA-Junos-User-Interfaces-CLI-Help.md)
  * [JNCIA-Junos | User Interfaces: CLI Filtering Output](202005252000-JNCIA-Junos-User-Interfaces-CLI-Filtering-Output.md)
  * [JNCIA-Junos | User Interfaces: Active versus Candidate Configuration](202005260819-JNCIA-Junos-User-Interfaces-Active-Versus-Candidate-Configuration.md)
  * [JNCIA-Junos | User Interfaces: Reverting to Previous Configuration](202005260853-JNCIA-Junos-User-Interfaces-Reverting-to-Previous-Configuration.md)
  * [JNCIA-Junos | User Interfaces: Adding and Removing Configuration Statements](202005260858-JNCIA-Junos-User-Interfaces-Adding-Removing-Configuration-Statements.md)
  * [JNCIA-Junos | User Interfaces: The J-Web Interface](202005260903-JNCIA-Junos-User-Interfaces-J-Web-Interface.md)
  * [JNCIA-Junos | Configuration Basics: Factory Default State](202005260925-JNCIA-Junos-Configuration-Basics-Factory-Default-State.md)