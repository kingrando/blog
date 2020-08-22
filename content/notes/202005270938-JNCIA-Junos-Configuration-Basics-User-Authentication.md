---
title: "JNCIA Junos | Configuration Basics: User Authentication"
date: 2020-05-27T09:38:44-05:00
tags:
  - JNCIA-Junos
categories:
  - Certifications
  - Juniper
  - Networking
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
    }
}
```

When creating a new local user, the following password requirements must be met:

* A minimum of 6 characters
* A mix of upper and lowercase characters
* Can include any alphanumeric number of special characters except control characters

### Local User Configuration

* Create a new user

  ```bash
  # Command
  set system login user <username> authentication plain-text-password
  # Example
  set system login user kameron authentication plain-text-password
  New password:
  Retype new password:
  ```

* Set the login class for a user

  ```bash
  # Command
  set system login user <username> class [<user-defined-class> | operator | read-only | super-user | authorized]
  # Example
  set system login user kameron class super-user
  ```

When a user is created, a working directory is created for that user.

* The root user's working directory is located at `/root`
* All other user directories are located at `/var/home/<username>`

If you want to change the working directory for a user, you can issue the following command:

```bash
# Command (Operational Mode)
set cli directory <directory>
# Example
set cli directory /tmp/var/my_new_working_directory
```
  
You can view the current working directory using:

```bash
# Command (Operational Mode)
kameron@RE4> show cli directory
Current directory: /var/home/kameron
```

## RADIUS and TACACS+

The other option for configuring user accounts is to use a AAA server which can either be RADIUS or TACACS+ but TACACS+ isn't very common outside of Cisco environments. The use of a AAA server allows for flexibility, scalability, and ease of user management.

### Login Classes with RADIUS

When RADIUS is used for authentication, the Junos device can apply a local user template to that user’s session. This template specifies what login class will be applied.

To create a local template, perform the following:

```bash
# Command
set system login user <template-name> class [<user-defined-class> | operator | read-only | super-user | authorized]
# Example
set system login user remote-=user class read-only
```

### Authentication Order

The authentication order is set using the `authentication-order` statement.

To set the authentication order issue the following command:

```bash
# Command
set system authentication-order <method or group of methods>
# Example
set system authentication-order [radius password]
```

To add an additional authentication method:

```bash
# Command
insert system authentication-order [password | radius | tacplus] [before | after] [password | radius | tacplus]
# Example
insert system authentication-order tacplus before password
```

To remove an authentication method:

```bash
# Command
delete system authentication-order [password | radius | tacplus]
# Example
delete system authentication-order tacplus
```

Authentication is done in the order that is set in the authentication-order command. If a login is not found in the radius or tacacs server then the local user database is tried.

RADIUS or TACACS+ authentication can fail because the authentication servers:

* Are not configured
* Do not respond within the timeout period
* Are not reachable over the network

### Configuring RADIUS

To configure RADIUS, you must issue the following commands:

  1. Add an IPv4 or IPv6 server address:

```bash
# Command
set system radius-server <server-address>
# Example
set system radius-server 10.0.0.1
```
  
  1. Set the shared secret

```bash
# Command
set radius-server <server-address> secret <secret>
# Example
set radius-server 10.0.0.1 secret Temp1234
```

  1. (Optional) Specify a port number

```bash
# Command
set radius-server <server-address> port <port-number>
# Example
set radius-server 10.0.0.1 port 1812
```
  
  1. Specify the authentication order

```bash
# Command
set system authentication-order [radius password]
```
  
  1. Assign a login class for remote users

```bash
# Command
set system login user <user-template-name> class <class>
# Example
set system login user remote class read-only
```
  
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
   user@host# show system authentication-order authentication-order [password | radius | tacplus]
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
