---
title: Error 'qmail: alert: cannot start: unable to open mutex'
description: 
published: true
date: 2021-07-24T05:26:00.620Z
tags: 
editor: markdown
dateCreated: 2021-07-24T05:26:00.620Z
---

# Error 'qmail: alert: cannot start: unable to open mutex'


If an error "qmail: alert: cannot start: unable to open mutex" is encountered while starting qmail.

Proceed with the following steps to fixing the error:-

Check the following logs.

```
tail -f /var/log/messages
tail -f /var/log/maillog
```

If you can't trace the error from log files, please run the binary from /var/qmail/bin.

```
[root@server]#cd /var/qmail/bin
[root@server]#./qmail-send
```

If the error is something like "alert: cannot start: unable to open mutex"

```
[root@server]# touch /var/qmail/queue/lock/sendmutex
[root@server]# chown qmails:qmail /var/qmail/queue/lock/sendmutex
```

Restart qmail using the command

```
[root@server]# /etc/rc.d/init.d/qmail start
```

