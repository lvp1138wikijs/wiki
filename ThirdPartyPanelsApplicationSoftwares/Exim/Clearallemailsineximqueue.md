---
title: Clear all emails in exim queue [Applicable to cPanel server]
description: 
published: true
date: 2021-07-24T05:34:08.417Z
tags: 
editor: markdown
dateCreated: 2021-07-24T05:34:08.417Z
---

# Clear all emails in exim queue [Applicable to cPanel server]


**Fastest solution to remove all emails in EXIM queue**

Follow the commands correctly under a cPanel server to clear / remove all the emails from the queue.

- cd /var/spool
- 
- mv exim exim.old
- 
- mkdir -p exim/input
- 
- mkdir -p exim/msglog
- 
- mkdir -p exim/db
- 
- chown -R mailnull:mail exim
- 
- /sbin/service exim restart


