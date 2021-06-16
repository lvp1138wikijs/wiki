---
title: How to fix "Unable to open logs" error while restarting apache
description: 
published: true
date: 2021-06-16T17:57:09.667Z
tags: 
editor: markdown
dateCreated: 2021-06-16T17:57:09.667Z
---

If you receive the following error while restarting Apache in the server, please try it out the following fix:

```
Unable to open logs
```

The low number of file descriptors are causing this issue. Check the current limit of file descriptors in the file /proc/sys/fs/file-max:

```
$ cat /proc/sys/fs/file-max
1024
```

If fs.file-max is quite small (several thousands or so), it should be changed to a higher value using the following command:

```
$ echo "65535" > /proc/sys/fs/file-max
```

If you want to make this changes permanent, you can add it to /etc/sysctl.conf as follows:


```
# Maximum number of open files permited
fs.file-max = 65535
```

To load new values from the sysctl.conf file use the following command:

```
$ sysctl -p /etc/sysctl.conf
```

Add `ulimit -n 65536` command to /etc/rc.d/init.d/httpd and /usr/sbin/apachectl apache startup scripts before other commands.

