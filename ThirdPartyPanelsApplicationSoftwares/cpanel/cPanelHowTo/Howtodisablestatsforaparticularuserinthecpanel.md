---
title: How to disable stats for a particular user in the cpanel
description: 
published: true
date: 2021-12-23T19:30:27.886Z
tags: 
editor: markdown
dateCreated: 2021-12-23T19:30:27.886Z
---

# How to disable stats for a particular user in the cpanel


To disable the stats service(Analog or Awstats or Webalizer stats) for a particular user in cpanel use the following steps.

1) Login to the server via ssh.

2) Add the following entries in the cpanel user file /var/cpanel/users/username (Replace "username"  with the name of user).

```
skipanalog=1

skipawstats=1

skipwebalizer=1
```

3) Now restart the cpanel service in the server.

```
/etc/init.d/cpanel restart
```