---
title: Forcefully Clearing the Qmail Queue
description: 
published: true
date: 2021-07-24T05:31:46.900Z
tags: 
editor: markdown
dateCreated: 2021-07-24T05:31:46.900Z
---

# Forcefully Clearing the Qmail Queue

If you have the need to forcefully delete everything in the qmail queue then do the following steps.

1. First run the following command to view the queue.

```
# /var/qmail/bin/qmail-qstat
messages in queue: 22463
messages in queue but not yet preprocessed: 22
```

2. Now stop the qmail service

```
/etc/init.d/qmail stop 
```
3. Then run the following commands

```
find /var/qmail/queue/mess -type f -exec rm {} \;
find /var/qmail/queue/info -type f -exec rm {} \;
find /var/qmail/queue/local -type f -exec rm {} \;
find /var/qmail/queue/intd -type f -exec rm {} \;
find /var/qmail/queue/todo -type f -exec rm {} \;
find /var/qmail/queue/remote -type f -exec rm {} \;
```
4. Now start the qmail server again and recheck the mail queue

```
/etc/init.d/qmail start
```

