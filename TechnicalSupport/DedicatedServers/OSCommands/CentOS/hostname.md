---
title: CentOS 7 | Command to change Hostname
description: 
published: true
date: 2021-12-22T13:31:36.251Z
tags: centos 7 hostname
editor: markdown
dateCreated: 2021-12-22T13:31:36.251Z
---

# CentOS 7 | Command to change Hostname

#### On a CentOS 7 server you can use "hostnamectl" tool to manage hostnames:
The hostname can be configured as follows:
1. Static host name assigned by sysadmin. For example, cp.serverpoint.com
2. Transient/dynamic host name assigned by DHCP or mDNS server at run time.
3. Pretty host name assigned by sysadmin/end-users and it is a free-form UTF8 host name for presentation to the user. For example, “My

Let us see how to use the hostnamectl command. Type the following in the command line:
`$ hostnamectl

OR

$ hostnamectl status`

Sample output:

`[root@lasvegas-nv-datacenter ~]# hostnamectl status
Static hostname: lasvegas-nv-datacenter.com
Icon name: computer-desktop
Chassis: desktop
Machine ID: 0ee5a22bac984d3585e2719bbbe1fe65
Boot ID: 35bba46f03ea4454ad7c746024e48f43
Operating System: CentOS Linux 7 (Core)
CPE OS Name: cpe:/o:centos:centos:7
Kernel: Linux 3.10.0-514.2.2.el7.x86_64
Architecture: x86-64`

###### How to set the host name?

The syntax is:

`# hostnamectl set-hostname Your-New-Host-Name`
`# hostnamectl set-hostname "Your New Host Name" --pretty`
`# hostnamectl set-hostname Your-New-Host-Name --static`
`# hostnamectl set-hostname Your-New-Host-Name --transient`

To set host name to cp.serverpoint.com

`hostnamectl set-hostname cp.serverpoint.com`
To set static host name to cp.serverpoint.com
`hostnamectl set-hostname cp.serverpoint.com --static`
To set pretty host name to “My cPanel Server”, enter:
`# hostnamectl set-hostname "My cPanel Server" `--pretty

##### To verify new settings, enter:

`# hostnamectl status`

Sample outputs:

[root@lasvegas-nv-datacenter ~]#
`hostnamectl status
Static hostname: cp.serverpoint.com
Icon name: computer-desktop
Chassis: desktop
Machine ID: 0ee5a22bac984d3585e2719bbbe1fe65
Boot ID: 35bba46f03ea4454ad7c746024e48f43
Operating System: CentOS Linux 7 (Core)
CPE OS Name: cpe:/o:centos:centos:7
Kernel: Linux 3.10.0-514.2.2.el7.x86_64
Architecture: x86-64`
##### How to delete a particular host name?
The syntax is:
`# hostnamectl set-hostname ""`
`# hostnamectl set-hostname "" --static`
`# hostnamectl set-hostname "" --pretty`