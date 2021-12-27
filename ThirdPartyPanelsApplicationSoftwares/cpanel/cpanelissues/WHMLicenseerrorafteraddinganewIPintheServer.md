---
title: WHM License error after adding a new IP in the Server
description: 
published: true
date: 2021-12-27T16:19:46.914Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:19:46.914Z
---

# WHM License error after adding a new IP in the Server


After adding a new IP address in a cPanel Server, while accessing WHM, it will start showing License related error as follows:

```
This copy of cPanel & WHM is for trial use and will expire at the end of the trial period. You will need to upgrade to a paid copy of cPanel & WHM to continue using the software after that period.
```

If you see trial license message in WHM, do the following steps:

```
1) Check if the IP is having active license or not from : http://verify.cpanel.net/
2) If it is showing active, you need to sync the license with cPanel server by using following command with "root" user only:
# /usr/local/cpanel/cpkeyclt
3) If license get synchronized without giving any error and still you are getting trial license message then it is possible to have incorrect Main IP.
4) Verify it using following command. It will most probably show the newly added IP.
curl -L http://cpanel.net/showip.cgi
lynx -dump http://cpanel.net/showip.cgi
```

If it shows different IP than the Main IP, then please do below given steps:

```
1. From backend, type ifconfig and find the interfaces in which the IP addresses are configured. The newly added IP will be configured in eth0 and the main IP in another interface.
1. In that case, open /etc/sysconfig/network-scripts/ifcfg-eth0 and change IP address to the main IP
1. Similarly open the file that contain the main IP and change IP to newly added one. 
```

The file will look as follows:

```
DEVICE=eth0:1
ONBOOT=yes
BOOTPROTO=static
IPADDR=64.235.x.x
NETMASK=255.255.255.0
```

Once changed both files with correct IPs, restart network.  Ensure all IP addresses are up.

```
/etc/init.d/network restart
```

Finally sync the license with cPanel server by using following command:

```
# /usr/local/cpanel/cpkeyclt
```

Refresh WHM, error will be gone 


