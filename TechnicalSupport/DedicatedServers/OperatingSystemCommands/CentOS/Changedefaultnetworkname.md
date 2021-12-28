---
title: Change default network name to old “eth0” on RHEL 7 / CentOS7 / Fedora 19 above
description: 
published: true
date: 2021-12-22T13:58:19.171Z
tags: network name, eth0
editor: markdown
dateCreated: 2021-12-22T13:58:19.171Z
---

# Change default network name to old “eth0” on RHEL 7 / CentOS7 / Fedora 19 above

First check the interface name using command ip addr show or ifconfig

> [root@lasvegas-nv-datacenter /]# ip addr show
> 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN
> link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
> inet 127.0.0.1/8 scope host lo
> valid_lft forever preferred_lft forever
> inet6 ::1/128 scope host
> valid_lft forever preferred_lft forever
>  
> 2: eno0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
> link/ether 0c:c4:7a:76:9a:68 brd ff:ff:ff:ff:ff:ff
> inet 64.235.48.24/24 brd 64.235.48.255 scope global dynamic eth0
> valid_lft 392sec preferred_lft 392sec
> inet6 fe80::ec4:7aff:fe76:9a68/64 scope link
> valid_lft forever preferred_lft forever
>  
> 3: en01: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
> link/ether 0c:c4:7a:76:9a:69 brd ff:ff:ff:ff:ff:ff
> inet6 fe80::ec4:7aff:fe76:9a69/64 scope link
> valid_lft forever preferred_lft forever
{.is-info}


So the interface names are en0 and en1. We need to change it to default eth0 and eth1. Do the following steps

Open  /etc/default/grub and look for this line “GRUB_CMDLINE_LINUX” and add the following: “net.ifnames=0 biosdevname=0”. Should look like this:

> GRUB_TIMEOUT=5
> GRUB_DISTRIBUTOR="$(sed 's, release .*$,,g' /etc/system-release)"
> GRUB_DEFAULT=saved
> GRUB_DISABLE_SUBMENU=true
> GRUB_TERMINAL_OUTPUT="console"
> GRUB_CMDLINE_LINUX="crashkernel=auto rhgb quiet net.ifnames=0 biosdevname=0"
> GRUB_DISABLE_RECOVERY="true"

Now run command to update grub config file 

> [root@lasvegas-nv-datacenter /]# grub2-mkconfig -o /boot/grub2/grub.cfg

Rename the interface files and restart server

> [root@lasvegas-nv-datacenter /]# mv /etc/sysconfig/network-scripts/ifcfg-eno0 /etc/sysconfig/network-scripts/ifcfg-eth0
> [root@lasvegas-nv-datacenter /]# mv /etc/sysconfig/network-scripts/ifcfg-eno1 /etc/sysconfig/network-scripts/ifcfg-eth1
> [root@lasvegas-nv-datacenter /]#  shutdown -r now
{.is-info}

After system boot then run command to confirm the changes

> [root@lasvegas-nv-datacenter /]# ip addr show
> 1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN
>     link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
>     inet 127.0.0.1/8 scope host lo
>        valid_lft forever preferred_lft forever
>     inet6 ::1/128 scope host
>        valid_lft forever preferred_lft forever
> 2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
>     link/ether 0c:c4:7a:76:9a:68 brd ff:ff:ff:ff:ff:ff
>     inet 64.235.48.24/24 brd 64.235.48.255 scope global dynamic eth0
>        valid_lft 473sec preferred_lft 473sec
>     inet6 fe80::ec4:7aff:fe76:9a68/64 scope link
>        valid_lft forever preferred_lft forever
> 3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP qlen 1000
>     link/ether 0c:c4:7a:76:9a:69 brd ff:ff:ff:ff:ff:ff