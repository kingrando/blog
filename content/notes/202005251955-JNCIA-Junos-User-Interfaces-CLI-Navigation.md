---
title: "JNCIA-Junos | User Interfaces: CLI Navigation"
date: 2020-05-25T19:55:26-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
---
## Command Completion

Junos OS provides two ways to complete commands using the CLI.

  1. Space Bar
     * **Example**: typing `set ch` followed by spacebar will complete the command to `set chassis`.
     * This can be disabled using the following command:
       * `set cli complete-on-space off`
  1. Tab
     * Completes commands and variables such as policy names, AS paths, community names, and IP addresses.
     * **Example**: if an interface has an IP address configured on it, the following command can be entered followed by tab: `set interface ge-0/0/0 unit 0 family inet address 1` , followed by tab and it will complete to `set interface ge-0/0/0 unit 0 family inet address 10.0.1.1/30` or whatever the IP address is set to.

## Editing Command Lines

The Junos OS uses a default VT100 terminal types for commands and arrow keys. The platform also supports emac commands for moving around the lines which include:

* `Ctrl+b` - Left one character
* `Ctrl+a` - Beginning of line
* `Ctrl+f` - Right one character
* `Ctrl+e` - End of line
* `Ctrl+d` - Deletes the character over the cursor
* `Ctrl+k` - Deletes from the cursor to the end of the line
* `Ctrl+u` - Deletes all characters and negates the current command
* `Ctrl+w` - Deletes the entire word to the left of the cursor
* `Ctrl+l` - Redraws the current line
* `Ctrl+p` - Repeats the previous command in the command history
* `Ctrl+n` - Repeats the next command in the command history
* `Esc+d` - Deletes the word to the right
* `Esc+b` - Moves the cursor back one word with no delete
* `Esc+f` - Moves the cursor forward one word with no delete

## Moving Between Levels

Since the Junos OS is a hierarchy configuration, you can move between the hierarchy levels. The following options are available to move between levels:

* `edit` - Used to specify your desired hierarchy level.

  ```bash
  [edit]
  kameron@RE4# edit interfaces ge-0/0/0

  [edit interfaces ge-0/0/0]
  kameron@RE4#
  ```

* `up` - Moves you up one level in the configuration.

  ```bash
  [edit interfaces ge-0/0/0 unit 0 family inet]
  kameron@RE4# up

  [edit interfaces ge-0/0/0 unit 0]
  kameron@RE4#
  ```

* `up n` - Moves you up the number placed at *n*.
  
  ```bash
  [edit interfaces ge-0/0/0 unit 0]
  kameron@RE4# up 2

  [edit interfaces]
  kameron@RE4#
  ```

* `top` - Moves to the top of the configuration hierarchy.

  ```bash
  [edit interfaces ge-0/0/0 unit 0 family inet]
  kameron@RE4# top

  [edit]
  kameron@RE4#
  ```

* `exit` - Returns the user to the most recent, higher level hierarchy.

  ```bash
  [edit interfaces ge-0/0/0]
  kameron@RE4# exit

  [edit]
  kameron@RE4#
  ```

## References

* [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
