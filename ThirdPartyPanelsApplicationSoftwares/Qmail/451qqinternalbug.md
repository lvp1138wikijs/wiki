---
title: 451 qq internal bug (#4.3.0)
description: 
published: true
date: 2021-07-24T05:15:05.171Z
tags: 
editor: markdown
dateCreated: 2021-07-24T05:15:05.171Z
---

# 451 qq internal bug (#4.3.0)

Plesk Qmail error – 451 qq internal bug

> Qmail Error! 
> qmail: 451 qq internal bug (#4.3.0) 
{.is-danger}

To eliminate this problem, stop Qmail process and replace qmail-queue, qmail-local and qmail-remote with the qmail-queue.moved, qmail-local.moved and qmail-remote.moved accordingly:

- cd /var/qmail/bin
- cp -p qmail-local.moved qmail-local
- cp -p qmail-remote.moved qmail-remote
- cp -p qmail-queue.moved qmail-queue

If you face any problems replacing these files, you can stop these processes forcibly and then try to replace them:

- killall qmail-remote qmail-queue qmail-local

Make sure that the permissions and ownersips are right:

- ls -la qmail-queue qmail-local qmail-remote

```

-r-xr-xr-x 1 root qmail 44060 Jun 13 2006 qmail-local
-r-s--x--x 1 qmailq qmail 15784 Jan 26 14:06 qmail-queue
-r-xr-xr-x 1 root qmail 43364 Jun 13 2006 qmail-remote
```



