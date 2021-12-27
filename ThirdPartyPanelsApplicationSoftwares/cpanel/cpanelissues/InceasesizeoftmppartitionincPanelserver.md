---
title: Incease size of /tmp partition in cPanel server.
description: 
published: true
date: 2021-12-27T15:29:41.596Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:29:41.596Z
---

# Incease size of /tmp partition in cPanel server.


In order to increase the size of /tmp partition in cpanel server, please do the following steps:

1) Edit the /scripts/securetmp file and look for the line tmpdsksize using vi editor and then change the size of the /tmp that you want.

```
my $tmpdsksize =512000;
```

2) Then stop the services chkservd, httpd and mysql using the following commands.

```
service chkservd stop
service httpd stop
service mysql stop
```

3)Then umount the /tmp and /var/tmp directories using the following commands.

```
umount -l /tmp
umount -l /var/tmp
```
4) Then create a nice new one:

```
/scripts/securetmp
```

5) Then mount the /tmp directory.

```
mount -l /tmp
```

6) Then restrt the services httpd, mysql and chkservd services.

```
service httpd start
service mysql start
service chkservd start
```

