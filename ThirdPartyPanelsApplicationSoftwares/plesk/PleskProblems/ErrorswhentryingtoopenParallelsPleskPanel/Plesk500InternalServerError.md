---
title: Plesk - 500 Internal Server Error
description: 
published: true
date: 2021-07-11T00:59:05.095Z
tags: 
editor: markdown
dateCreated: 2021-07-11T00:59:05.095Z
---

**If you are getting the error "500 Internal Server Error." on plesk**.

**Symptoms**

**Error on Plesk Panel**:

> 500 Internal Server Error.
{.is-danger}


**Error on shell while trying to restart apache / PSA from shell**:

```
root@server:~# /etc/init.d/apache2 stop
-bash: /etc/init.d/apache2: /bin/sh: bad interpreter: No such file or directory
 
 
root@server:/etc/php5/apache2# /etc/init.d/psa status
sw-cp-serverd (pid 1538) is running...
 
root@server:/etc/php5/apache2# /etc/init.d/psa stop
Stopping psa...                                                       done
 
root@server:/etc/php5/apache2# /etc/init.d/psa start
Starting xinetd service...                                            failed
Starting mysql service...                                             failed
Starting bind9 service...                                             failed
Starting postgresql service...                                        not installed
Starting psa-spamassassin service...                                  not installed
Plesk: Starting Mail Server...                                        failed
Service /etc/init.d/apache2 failed to start
 
System error 2: No such file or directory
Service /etc/init.d/apache2 failed to stop
 
System error 2: No such file or directory
Service /etc/init.d/apache2 failed to start
 
System error 2: No such file or directory
websrvmng: /opt/psa/admin/sbin/apache_control_adapter execution failed:
Service /etc/init.d/apache2 failed to start
 
System error 2: No such file or directory
Service /etc/init.d/apache2 failed to stop
 
System error 2: No such file or directory
Service /etc/init.d/apache2 failed to start
 
System error 2: No such file or directory
websrvmng: /opt/psa/admin/sbin/apache_control_adapter execution failed:
Service /etc/init.d/apache2 failed to start
 
System error 2: No such file or directory
Service /etc/init.d/apache2 failed to stop
 
System error 2: No such file or directory
Service /etc/init.d/apache2 failed to start
 
System error 2: No such file or directory
Starting psa...                                                       failed
root@server:/etc/php5/apache2# /etc/init.d/apache2 restart
-bash: /etc/init.d/apache2: /bin/sh: bad interpreter: No such file or directory
root@server:/etc/php5/apache2# ls /etc/init.d
apache2        drwebd             networking                   postfix          screen-cleanup          udevmonitor
apparmor       friendly-recovery  network-interface            pppd-dns         sendsigs                udevtrigger
apport         grub-common        network-interface-container  procps           setvtrgb                ufw
atd            halt               network-interface-security   psa              single                  umountfs
bind9          hostname           ondemand                     rabbitmq-server  skeleton                umountnfs.sh
bluetooth      hwclock            passwd                       rc               ssh                     umountroot
bootlogd       hwclock-save       pc-remote                    rc.local         stop-bootlogd           urandom
console-setup  irqbalance         plymouth                     rcS              stop-bootlogd-single    x11-common
courier-imap   killprocs          plymouth-log                 README           sudo                    xinetd
cron           mailerq            plymouth-ready               reboot           sw-cp-server
dbus           mailman            plymouth-splash              resolvconf       udev
dmesg          module-init-tools  plymouth-stop                rsync            udev-fallback-graphics
dns-clean      mysql              plymouth-upstart-bridge      rsyslog          udev-finish
root@server:/etc/php5/apache2# ls /bin
bash          chvt                  fgconsole       lesskey     nc                ntfsmove                 sed              unicode_start
bunzip2       cp                    fgrep           lesspipe    nc.openbsd        ntfstruncate             setfacl          vdir
busybox       cpio                  findmnt         ln          netcat            ntfswipe                 setfont          which
bzcat         dash                  fuser           loadkeys    netstat           open                     setupcon         whiptail
bzcmp         date                  fusermount      login       nisdomainname     openvt                   sleep            ypdomainname
bzdiff        dbus-cleanup-sockets  getfacl         lowntfs-3g  ntfs-3g           pidof                    ss               zcat
bzegrep       dbus-daemon           grep            ls          ntfs-3g.probe     ping                     static-sh        zcmp
bzexe         dbus-uuidgen          gunzip          lsblk       ntfs-3g.secaudit  ping6                    stty             zdiff
bzfgrep       dd                    gzexe           lsmod       ntfs-3g.usermap   plymouth                 su               zegrep
bzgrep        df                    gzip            mkdir       ntfscat           plymouth-upstart-bridge  sync             zfgrep
bzip2         dir                   hostname        mknod       ntfsck            ps                       tailf            zforce
bzip2recover  dmesg                 init-checkconf  mktemp      ntfscluster       pwd                      tar              zgrep
bzless        dnsdomainname         initctl2dot     more        ntfscmp           rbash                    tempfile         zless
bzmore        domainname            ip              mount       ntfsdecrypt       readlink                 touch            zmore
cat           dumpkeys              kbd_mode        mountpoint  ntfsdump_logfile  rm                       true             znew
chacl         echo                  kill            mt          ntfsfix           rmdir                    ulockmgr_server
chgrp         ed                    less            mt-gnu      ntfsinfo          rnano                    umount
chmod         egrep                 lessecho        mv          ntfsls            running-in-container     uname
chown         false                 lessfile        nano        ntfsmftalloc      run-parts                uncompress
```

**Error on server logs**:

```
root@server:~# tail -5 /var/log/sw-cp-server/error_log
2013-06-28 13:15:49: (mod_fastcgi.c.3962) pid  13387 5 not found: No child processes
2013-06-28 13:15:50: (mod_fastcgi.c.3962) pid  20997 5 not found: No child processes
2013-06-28 13:15:50: (mod_fastcgi.c.3962) pid  13387 5 not found: No child processes
2013-06-28 13:15:51: (mod_fastcgi.c.3962) pid  20997 5 not found: No child processes
2013-06-28 13:15:51: (mod_fastcgi.c.3962) pid  13387 5 not found: No child processes
```

**Cause**:

> Customer might have accidentally deleted the file "/bin/sh" from the server.
{.is-info}


**Resolution**:

create a link to the file /bin/sh from shell

```
root@server:~# which bash
-bash: /usr/bin/which: /bin/sh: bad interpreter: No such file or directory
 
root@server:~# ln -s /bin/bash /bin/sh
 
root@server:~# which bash
/bin/bash
root@server:~# /etc/init.d/apache2 restart
* Restarting web server apache2 ... waiting [ OK ]
 
root@server:~# /etc/init.d/psa restart
```


