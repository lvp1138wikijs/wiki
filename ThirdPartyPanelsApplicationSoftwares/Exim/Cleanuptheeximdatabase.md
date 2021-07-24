---
title: Clean up the exim database
description: 
published: true
date: 2021-07-24T23:09:31.385Z
tags: 
editor: markdown
dateCreated: 2021-07-24T23:09:31.385Z
---

# Clean up the exim database

If you will find lots of junk e-mail messages sitting around in Exim db that cannot be delivered to the recipient for some reason or another.

The end result is a bunch of messages in the your exim_mainlog showing as RETRY, UNDELIVERABLE, SMTP TIMEOUT etc. But you can cleanup that junk by following the instructions below:

```
/usr/sbin/exim_tidydb -t 1s /var/spool/exim retry
/usr/sbin/exim_tidydb -t 1s /var/spool/exim wait-remote_smtp
```

Copy and paste these commands and then press enter. Watch the junk dissappear. You will see loads of junk being deleted.

