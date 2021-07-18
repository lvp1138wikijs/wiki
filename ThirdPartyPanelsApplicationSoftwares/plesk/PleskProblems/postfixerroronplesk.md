---
title: postfix error on plesk
description: 
published: true
date: 2021-07-18T05:20:03.853Z
tags: 
editor: markdown
dateCreated: 2021-07-18T05:20:03.853Z
---

# postfix error on plesk

**Error Message**:

> An error occurred while sending mail. The mail server responded: 4.3.0 Error: queue file write error.
{.is-info}

**Solution**:

> It can be caused by exceeding the mail box quota of some email accounts. Check the quota and find the user account.
> 
{.is-info}

Open the PostFix configuration file

```
/etc/postfix/master.cf
```
Replace the line

```
smtp inet n - - - - smtpd -o smtpd_proxy_filter=127.0.0.1:10025
```
with

```
smtp inet n - n - - smtpd
```

Make sure that the first line is commented out. If both lines exists on the conf at the same time the following error will be displayed

> server:~# /etc/init.d/postfix reload
> 
> [....] Reloading Postfix configuration...postfix/postfix-script: fatal: the Postfix mail system is not running
> 
> failed.
{.is-danger}


Restart the PostFix service.

```
/etc/init.d/postfix restart
```

Ref: http://worldofadmins.blogspot.in/2012/06/postfix-in-plesk-451-430-error-queue.html

