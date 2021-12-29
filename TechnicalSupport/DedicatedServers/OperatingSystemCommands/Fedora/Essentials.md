---
title: Essentials in Fedora
description: 
published: true
date: 2021-12-29T13:56:41.770Z
tags: essentials in fedora
editor: markdown
dateCreated: 2021-12-29T12:33:53.249Z
---

# Fedora

### Drive label
From Fedora core 7, FC8 and FC9, FC10 all use drive labels to recongnize the drive. If Fedora is not booting then you have to check either the correct labels are assgined to the the drives in /boot/grub/grub.conf and /etc/fstab or not.

- Open the /boot/grub/grub.conf.

`vi /boot/grub/grub.conf`

- it should have following in the kernal line.

> root=LABEL=/
>  
> If it have,
> root=/dev/hda1 or root=/dev/sda1
> then correct it as above.
> 
{.is-info}

- Open /etc/fstab.

> vi /etc/fstab
{.is-info}

 - it should have lines as below.
 
>  LABEL=/
> LABEL=/boot
> LABEL=swap
> Instead of
> /dev/hda1
> /dev/hda2
> /dev/hda3
{.is-info}


### Correcting network settings
 - After correcting grub setting, you might need to correct IP and mac address setting as well.

 - For IP address, you need to check gateway at /etc/sysconfig/network and ip address in
 /etc/sysconfig/network-scripts/ifcfg-eth0

 - For Mac, you need to check /etc/udev/rules.d/70-persistent-net.rules and make sure MAC address is correct at
 

SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1b:21:27:9d:3e", ATTR{type}=="1", NAME="eth0"

 **If it is not correct then delete incorrect mac address from above line and write correct mac address. You can get correct mac address by doing ifconfig in server**


### Clearing udev
 - In case, drive is moved to new server or logs show UDEV error, netboot server and mount paritions.

 - then go to /etc/udev and clear the file

cat /dev/null >70-persistent-net.rules

- Reboot server normally.



### Server Stop Responding while changing IPs

FC13 have a service NetworkManager, which automatically try to manage the network. Stop that service and set it to Not start on boot

Service NetworkManager stops chkconfig –del NetworkManager
Then set the usual network service to start on boot.
 

> Service Network Restart
> chkconfig --level 3 network on
> chkconfig --level 4 network on
> chkconfig --level 5 network on 
{.is-info}


## Fedora18


Fedora18 is an OS for which we get a very few orders therefore we do not have automatic image for it and a manual install is required. More over, it is slightly different structure then old versions of fedora or centos/redhat.

Configuring multiple network interface in Fedora18
fedora18 do not use eth0 for network names, rather it is p?p1 name and use NetworkManager service to manager it. (you can replace ? with some number which fedora choose different number for differnet machines, like p1p1, or p12p1, etc.)

1) To configure the network interface in fedore18, you will need to first change the network name p1p1 to eth0. Rename /etc/network/sysconfig/ifcfg-p1p1 as  /etc/network/sysconfig/ifcfg-eth0

2) Then execute the following command

yum remove biosdevname
3) Reboot the machine to make the changes in effect.

After reboot, you will see p1p1 replaced with eth0 you can confirm it by running ifconfig command.

4) Now to add additional ips you need to run the following command

> 
> ifconfig eth0:1 ip netmask 255.255.255.0
> 
> ifconfig eth0:2 ip netmask 255.255.255.0
> 
> Replace Ip with the actual ipaddress of the server. For example:
> 
> ifconfig eth0:1 64.235.52.56 netmask 255.255.255.0
> 
> ifconfig eth0:2 64.235.52.56 netmask 255.255.255.0
> 
{.is-info}


After adding the ipaddress verify it using the command ifconfig.
