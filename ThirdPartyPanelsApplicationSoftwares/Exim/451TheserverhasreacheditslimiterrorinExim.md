---
title: 451-The server has reached its limit error in Exim
description: 
published: true
date: 2021-07-24T22:54:49.923Z
tags: 
editor: markdown
dateCreated: 2021-07-24T22:54:49.923Z
---

# 451-The server has reached its limit error in Exim

For the error "451-The server has reached its limit for processing requests from your host" when you trying to telnet to port 25 (SMTP), please do the following steps:

1) To clear the ratelimit database use:

```
rm -f /var/spool/exim/db/ratelimit*
```

2) Then restart exim

```
service exim restart
```
or

```
/etc/init.d/exim restart
```

