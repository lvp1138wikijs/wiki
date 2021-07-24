---
title: ratelimit database not available
description: 
published: true
date: 2021-07-24T23:52:57.293Z
tags: 
editor: markdown
dateCreated: 2021-07-24T23:52:57.293Z
---

# ratelimit database not available

Seeing this in the logs /var/log/exim_mainlog

Berkeley DB error: __fop_file_setup:  Retry limit (100) exceeded
2011-01-21 00:13:17 failed to open DB file /var/spool/exim/db/ratelimit: Bad file descriptor
2011-01-21 00:13:17 H=web31602.mail.mud.yahoo.com [68.142.198.148] temporarily rejected connection in "connect" ACL: ratelimit database not available
2011-01-21 00:13:20 1PgC7M-0001VO-9H alt1.gmail-smtp-in.l.google.com [74.125.95.27] Connection refused
2011-01-21 00:13:21 Berkeley DB error: __fop_file_setup:  Retry limit (100) exceeded
2011-01-21 00:13:21 failed to open DB file /var/spool/exim/db/ratelimit: Bad file descriptor
2011-01-21 00:13:21 H=mail.homemark.co.za [196.36.136.10] temporarily rejected connection in "connect" ACL: ratelimit database not available
2011-01-21 00:13:22 Berkeley DB error: __fop_file_setup:  Retry limit (100) exceeded
Then run the following commands to resolve this issue,


```
rm -fv /var/spool/exim/db/*
/etc/init.d/exim restart
```