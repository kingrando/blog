---
title: "JNCIA Junos | Configuration Basics: User Authentication"
date: 2020-05-27T09:38:44-05:00
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
## Local Accounts
All new users that are created locally are added under the `[edit system login]` hierarchy.

```bash
system {
    login {
        user kameron {
            uid 2000;
            class super-user;
            authentication {
                encrypted-password ""; ## SECRET-DATA
            }
        }
```

When creating a new local user, the following password requirements must be met:

  * A minimum of 6 characters
  * A mix of upper and lowercase characters
  * Can include any alphanumeric number of special characters except control characters

**Local User Configuration**
  * Create a new user
    * `set system login user <username> authentication plain-text-password`
  * Set the login class for a user
    * `set system login user <username> class [<user-defined-class> | operator | read-only | super-user | authorized]`

When a user is created, a working directory is created for that user. 
  * The root user's working directory is located at `/root`
  * All other user directories are located at `/var/home/<username>`

If you want to change the working directory for a user, you can issue the following command:
  * `root@RE1> set cli directory directory`

## RADIUS and TACACS+
The other option for configuring user accounts is to use a AAA server which can either be RADIUS or TACACS+ but TACACS+ isn't very common outside of Cisco environments. The use of a AAA server allows for flexibility, scalability, and ease of user management. 

### Login Classes with RADIUS
When RADIUS is used for authentication, the Junos device can apply a local user template to that user’s session. This template specifies what login class will be applied. 

To create a local template, perform the following:
  * `set system login user <template-name> class [<user-defined-class> | operator | read-only | super-user | authorized]`
  * `set system login user remote-read-only class read-only`

### Authentication Order
The authentication order is set using the `authentication-order` statement. 

To set the authentication order issue the following command: 
  * `set system authentication-order [password | radius | tacplus]`
To add an additional authentication method:
  * `insert system authentication-order password [before | after] radius`
To remove an authentication method:
  * `delete system authentication-order password [before | after] radius`
 
Authentication is done in the order that is set in the authentication-order command. If a login is not found in the radius or tacacs server then the local user database is tried. 
 
RADIUS or TACACS+ authentication can fail because the authentication servers:
  * Are not configured.
  * Do not respond within the timeout period
  * Are not reachable over the network

### Configuring RADIUS
To configure RADIUS, you must issue the following commands:
  1.  Add an IPv4 or IPv6 server address:
    * set system radius-server server-address source-address source-address
  1. Set the shared secret
    * [edit system radius-server server-address]
    * set secret secret
  1. (Optional) Specify a port number
    * [edit system radius-server server-address]
    * set port port-number
  1. Specify the authentication order
    * set system authentication-order radius 
    * insert system authentication-order password after radius
  1. Assign a login class for remote users
    * set system login user remote class class

#### Setup FreeRADIUS for testing
Setup the FreeRADIUS server using the Getting Started guide found [here](https://wiki.freeradius.org/guide/Getting%20Started).

 Edit the file `/etc/freeradius/3.0/clients.conf` and add the switch or router:
 ```bash
client re1 {
        ipaddr = 192.168.30.52
        secret = juniper1234
}
```
Edit the file `/etc/freeradius/3.0/users.conf` and add the test user:
```bash
labreadonly     Cleartext-Password := "readonly"
                Service-Type = Login-User,
                Juniper-Local-User-Name := "remote-read-only"
```
After restarting the FreeRADIUS server then you should be able to test the user.


On the RADIUS server, the Juniper VSA (Vendor-Specific-Attribute) of Juniper-Local-User-Name must be set for the user. This attribute is used to match the user to the local user template.  

### Confirm RADIUS
  * Display the configured authentication order
    ```bash
    [edit]
    user@host# show system authentication-order authentication-order [password | radius | tacplus];
    ```
  * Display the configured radius-server
    ```bash
    [edit]
    user@host# show system radius-server
    192.168.30.12 {
        secret Radiussecret1;
        source-address 192.168.30.52;
    }
    ```
  * Display the configured TACACS+ server
    ```bash
    [edit]
    user@host# show system tacplus-server
    192.168.30.12 {
        secret Tacacssecret1;
        source-address 192.168.30.52;
    }
    ```

## References
  * [Juniper Open Learning: Junos, Associate](https://cloud.contentraven.com/junosgenius/learningpath-detail/1004/3/0/1)
  * [Configuration Example -- How to assign a login class to users that are authenticated using a FreeRADIUS server](https://kb.juniper.net/InfoCenter/index?page=content&id=KB19446)