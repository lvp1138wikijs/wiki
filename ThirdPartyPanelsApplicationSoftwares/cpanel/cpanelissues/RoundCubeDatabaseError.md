---
title: RoundCube Database Error
description: 
published: true
date: 2021-12-27T16:03:37.023Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:03:37.023Z
---

# RoundCube Database Error


cPanel RoundCube mail client is showing data base error when accessing through browser.

**Error Message**

```
DATABASE ERROR: CONNECTION FAILED!

Unable to connect to the database!
Please contact your server-administrator.
```

**Error Log in  /var/lib/mysql/hostname.err**

```
130505 22:27:51 InnoDB: Error: unable to create temporary file; errno: 13
130505 22:27:51 [ERROR] Plugin 'InnoDB' init function returned error.
130505 22:27:51 [ERROR] Plugin 'InnoDB' registration as a STORAGE ENGINE failed.
130505 22:27:51 [ERROR] Unknown/unsupported storage engine: InnoDB
```

**Fix**

The permissions on /tmp are messed up. Correct the permission and restart the mysql service again

```
chmod 1777 /tmp
/etc/init.d/mysql restart
```

