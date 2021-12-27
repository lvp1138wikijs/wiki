---
title: POP3 Authorizations Issues in Cpanel Server
description: 
published: true
date: 2021-12-27T16:01:32.866Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:01:32.866Z
---

# POP3 Authorizations Issues in Cpanel Server

If the email account are not able to login to the server using pop3, It could be because there is another pop3 server under xinetd being active.

The problem is xinted had two services popa3d and popa3ds, which were interfering with cpanel secure ports as well cpanel's pop3 service.

To fix this issue you can follow the steps given below.

1) Remove popa3d and popa3ds from /etc/xinetd.d folder

```
$ mv /etc/xinetd.d/popa3d   /backup/popa3d.bak

$ mv /etc/xinetd.d/popa3ds  /backup/popa3ds.bak
```

2) Restart xinetd service

```
 /etc/init.d/xinetd restart
```

3) Re-install the courier pop3 service.

```
/scripts/courierup --force
```



