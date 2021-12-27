---
title: MySQL Socket Error in phpMyAdmin
description: 
published: true
date: 2021-12-27T15:52:31.328Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:52:31.328Z
---

# MySQL Socket Error in phpMyAdmin


While accessing phpMyAdmin, you may get the following error.

```
#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)
```

1) This is due to the missing socket file in the location /tmp. Find the specified mysql socket file from the phpmyadmin configuration file.

In default cpanel install the socket path which is specified in the phpMyAdmin configuration file is /tmp/mysql.sock

```
$ vi /usr/local/cpanel/base/3rdparty/phpMyAdmin/config.inc.php

cfg['Server']['socket']         = '/tmp/mysql.sock';
```

2) Verify whether the files exists, If mysql.sock is missing in /tmp, then create a link to the mysql.sock file in /var/lib/mysql.

```
$ ln -s /var/lib/mysql/mysql.sock /tmp/mysql.sock
```

Once the socket file is added phpmyadmin will be working fine.

