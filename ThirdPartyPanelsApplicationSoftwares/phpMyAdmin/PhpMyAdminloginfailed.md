---
title: PhpMyAdmin login failed
description: 
published: true
date: 2021-12-21T17:49:56.469Z
tags: 
editor: markdown
dateCreated: 2021-12-21T17:49:56.469Z
---

# PhpMyAdmin login failed

Getting login failed error or getting phpmyadmin login window while login to the phpMyAdmin through cPanel, a force upgrading phpMyAdmin will fix the issue. In order to do that, please do the following steps:

1. SSH to your server as root and update phpmyadmin :

```
#/usr/local/cpanel/bin/updatephpmyadmin --force
```

2. If the issue is only for one user, do the following steps:

- Log into WHM and go to  Account Functions »Password Modification.
- Select user account and update password with the same as current on

**Note**: While updating password for user make sure "**Allow MySQL password change**" option is checked.
