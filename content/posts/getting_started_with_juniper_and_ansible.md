---
title: "Getting started with Juniper and Ansible"
date: 2020-08-17T12:28:57-05:00
draft: true
categories:
  - Automation
  - Networking
tags:
  - Ansible
  - Juniper
---
In this post I'm going to over how to install and setup Ansible, specifically to work with Juniper devices, and gather device information using Ansible.

## Setting up Ansible

To get started we need to install Ansible on our workstation or server. To install Ansible we need to have a computer running a supported OS such as Debian, CentOS, RedHat, BSD, or MacOS. We also need to have Python 2.7 or Python 3.5 or later install. I recommend sticking with Python 3.5 since Python 2.7 is deprecated.

I'm going to be using Ubuntu in this guide, but you can find information regarding your OS [here](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html#prerequisites)

The first thing we need to do is ensure we have Python 3.5 or later and the Python Package Manager (pip) installed. Issue the following two command (highlighted below):

{{< highlight bash "hl_lines=1 3" >}}
python3 --version
Python 3.6.9
pip3 --version
pip 20.2.1 from /usr/local/lib/python3.6/dist-packages/pip (python 3.6)
{{< /highlight >}}

If you do not have at least Python 3.5 installed and pip, you can issue the following commands:

{{< highlight bash >}}
sudo apt update
sudo apt install python3 -y
sudo apt install python3-pip -y
{{< /highlight >}}

After Python3 and pip are installed we can install ansible by issuing the following command:

{{< highlight bash >}}
pip3 install ansible
{{< /highlight >}}

The above install method was gathered from [here](https://docs.ansible.com/ansible/latest/reference_appendices/python_3_support.html). This ensures we install Ansible to work with Python3 by default.

Next we need to ensure we can run the ansible executable. To do this issue the following two commands:

{{< highlight bash >}}
# Add the local bin folder to your PATH
export PATH=$PATH:./.local/bin
# Verify that ansible works
ansible --version 
{{< /highlight >}}

The last item we need to install is the Juniper PyEZ Python module so we can use the **junos_collection**. Issue the following command:

{{< highlight bash >}}
pip3 install junos-eznc
{{< /highlight >}}

Now we are ready to setup our Ansible inventory. 

## Setting up our Inventory

By default, Ansible uses the concept of `hosts` file to manage your inventory. This is just a simple text file that outlines what our hosts, or equipment, are and what groups they belong to. The `hosts` file also outlines any variables to use in our playbooks.

To view the default configuration, open the following file in your text editor.

{{< highlight bash >}}
sudo vim /etc/ansible/hosts
{{< /highlight >}}

You should see something like this:

{{< highlight vim >}}
# This is the default ansible 'hosts' file.
# 
# It should live in /etc/ansible/hosts
#
#   - Comments begin with the '#' character
#   - Blank lines are ignored
#   - Groups of hosts are delimited by [header] elements
#   - You can enter hostnames or ip addresses
#   - A hostname/ip can be a member of multiple groups

# Ex 1: Ungrouped hosts, specify before any group headers.

## green.example.com
## blue.example.com
## 192.168.100.1
## 192.168.100.10

# Ex 2: A collection of hosts belonging to the 'webservers' group

## [webservers]
## alpha.example.org
## beta.example.org
## 192.168.1.100
## 192.168.1.110

# If you have multiple hosts following a pattern you can specify
# them like this:

## www[001:006].example.com

# Ex 3: A collection of database servers in the 'dbservers' group

## [dbservers]
## 
## db01.intranet.mydomain.net
## db02.intranet.mydomain.net
## 10.25.1.56
## 10.25.1.57

# Here's another example of host ranges, this time there are no
# leading 0s:

## db-[99:101]-node.example.com
{{< /highlight >}}

As I prefer YAML to INI format, I'm going to delete the default hosts file and generate a new one in YAML to support my lab network. The new hosts file looks like this:

{{< highlight yaml >}}
---
all:
  children:
    building_1:
      hosts:
        re1:
        re2:
    building_2:
      hosts:
        re3:
    building_3:
      hosts:
        re4:
        re5:
{{< /highlight >}}

Then we will rename the file using:

{{< highlight bash >}}
sudo mv /etc/ansible/hosts /etc/ansible/hosts.yaml
{{< /highlight >}}

Using the hosts file, we can call on hosts in our inventory using the `all` keyword, a group such as `building_1`, or the individual host such as `re1`.

The last step before we can test is to set update the default inventory file in the `ansible.cfg` file. Issue the following command:

{{< highlight bash >}}
sudo sed -i '/#inventory      = /etc/ansible/hosts/c\inventory      = /etc/ansible/hosts.yaml' /etc/ansible/ansible.cfg 
{{< /highlight >}}

Now that we have our `hosts` file setup, we can go ahead and test using an adhoc command. This just lets us verify that Ansible is working and that our hosts file is readable.

We can verify this by using the following command to ping all our hosts.

{{< highlight bash >}}
ansible all -m ping

{{< /highlight >}}
