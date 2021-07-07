---
title: DrWeb failure emails
description: 
published: true
date: 2021-07-07T23:44:19.548Z
tags: 
editor: markdown
dateCreated: 2021-07-07T23:44:19.548Z
---

In servers with the Plesk control panel when you encounter the issue of DrWeb failure emails follow these steps:

Edit the  below file:

```
/etc/drweb/drweb32.ini

```
Change the value of CronSummary from yes to no

```
CronSummary = yes
```

Finally restart the drewbd daemon

```
service drwebd restart
```