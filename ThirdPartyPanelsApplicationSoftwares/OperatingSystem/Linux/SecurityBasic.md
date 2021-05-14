---
title: Security:Basic
description: 
published: true
date: 2021-05-14T23:57:33.163Z
tags: 
editor: markdown
dateCreated: 2021-05-14T23:57:33.163Z
---

# Rkhunter

Rkhunter
 

Rkhunter or root kit hunter can be easily installed in linux. You just have to unpack the tar ball and install the rkhunter package.

To run rkhunter issue th efollowing command:

```
rkhunter -c --createlogfile
```

This will create a log file /var/log/ called rkhunter.log which will contain all details regarding damages and security threats.

 

Rkhunter hash checks all the binaries in your server. You can also run rkhuter using a cron job after disabling the interactive mode.

