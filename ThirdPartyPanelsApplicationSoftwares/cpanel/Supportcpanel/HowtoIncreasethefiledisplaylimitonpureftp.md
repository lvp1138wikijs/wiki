---
title: How to Increase the file display limit on pure-ftp
description: 
published: true
date: 2021-12-27T19:56:17.839Z
tags: 
editor: markdown
dateCreated: 2021-12-27T19:56:17.839Z
---

# How to Increase the file display limit on pure-ftp

By default, pure-ftp has a file display limit of 2000 files. In order to increase the file display limit on pure-ftp, please do the following steps: 


1) Log into your account via SSH as root user.

2) Open pure-ftp configuration file /etc/pure-ftp.conf using vi editor and search for the line LimitRecursion 2000 8 .

3) The first number after LimitRecursion is the display limit of files pure-ftp will show at anyone time. Change it to whatever values you feel is necessary for your server. The second number is the max subdirectory depth shown. You may change this value if necessary as well.

4) Restart the pure-ftpd service using the command:

```
service pure-ftpd restart
```