---
title: How to Enable Quota in the Server
description: 
published: true
date: 2021-12-23T19:33:41.893Z
tags: 
editor: markdown
dateCreated: 2021-12-23T19:33:41.893Z
---

# How to Enable Quota in the Server

If quotas are not enabled for the partition, the following error will occur while doing a quotacheck in the server.

In case of Cpanel server, /scripts/initquotas will throw the following error.

```
/scripts/initquotas
Quotas are now on
Updating Quota Files......
        quotacheck: Can't find filesystem to check or filesystem not mounted with quota option.
        quotacheck: Can't find filesystem to check or filesystem not mounted with quota option.
....Done
```

In order to fix this error, please do the following steps:

```
$ touch /quota.user /quota.group
$ chmod 600 /quota.*
$ mount -o remount /
$ quotaoff -a
$ vi /etc/fstab
 ( open 'fstab' file and add usrquota,grpquota to the partition where you want to have quota on. That is, for example, add the entry like:
/dev/ubd0 / ext3 defaults,noatime,usrquota,grpquota 1 0 )
$ quotaon -a
```

Then you can execute the script successfully without any errors. You can run a quotacheck in the server. In Cpanel server, you can run initquotas without any errors.