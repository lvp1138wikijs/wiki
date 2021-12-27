---
title: Bug in Mailman
description: 
published: true
date: 2021-12-27T14:31:18.066Z
tags: 
editor: markdown
dateCreated: 2021-12-27T14:31:18.066Z
---

# Bug in Mailman


While accessing the mailman, you may get the following error.

```
Bug in Mailman version 2.1.9.cp2

We're sorry, we hit a bug! Please inform the webmaster for this site of this problem. Printing of traceback and other system information has been explicitly inhibited, but the webmaster can find this information in the Mailman error logs.
```

One of the reason for the issue is that the folders in /usr/local/cpanel/3rdparty/mailman is not having sufficient permission

In order to fix this issue, please do the following steps:

```
$ ls -al /usr/local/cpanel/3rdparty/mailman
```

Then correct the permission using the following command:

```
$ chmod -R 2775 ./*
```

If it is not fix the error, you can try running the fixmailman script in the server at /scripts.

