---
title: Plesk DNS service does not start
description: 
published: true
date: 2021-07-11T00:31:06.570Z
tags: 
editor: markdown
dateCreated: 2021-07-11T00:31:06.570Z
---

**Symptoms**

1. DNS service does not start at "Tools & Settings > Services Management":

Error: Unable to make action: Unable to manage service by dnsmng: dnsmng: Service /etc/init.d/bind9 failed to start ('--start', 'dns')
 
2. Messages in /var/log/syslog indicate that /usr/sbin/named process has been denied access to files:

Jul 31 20:51:51 server kernel: [72092.073422] type=1400 audit(1375296711.625:24): apparmor="DENIED" operation="open" parent=22090 
profile="/usr/sbin/named" name="/var/named/run-root/usr/lib/x86_64-linux-gnu/openssl-1.0.0/engines/libgost.so" pid=22091 comm="named" 
requested_mask="r" denied_mask="r" fsuid=107 ouid=0

**Cause**

The problem is that Apparmor is stopping bind9 from accessing what it needs to run with Plesk's configuration. Parrallels advises to uninstall Apparmor  but instead of that we created allow rules to bind9's Apparmor  profile.

**Resolution**

Add the following the rules to the config file /etc/apparmor.d/local/usr.sbin.named

/var/log/query.log rw,
/var/named/run-root/** rwm,

and then run following commands

service apparmor reload
/etc/init.d/bind9 restart

