---
title: How to recreate /etc/userdomains when it is accidentally deleted or missing
description: 
published: true
date: 2021-12-23T19:55:59.183Z
tags: 
editor: markdown
dateCreated: 2021-12-23T19:55:59.183Z
---

# How to recreate /etc/userdomains when it is accidentally deleted or missing


cPanel has many scripts in /usr/local/cpanel/bin/ directory. The following script will help you to regenerate /etc/userdomains file.

Note: If any existing /etc/userdomains file in the server, delete or move it first before executing following scripts.


```
/usr/local/cpanel/bin/userdata_update
```

and then run

```
/scripts/updateuserdomains
```