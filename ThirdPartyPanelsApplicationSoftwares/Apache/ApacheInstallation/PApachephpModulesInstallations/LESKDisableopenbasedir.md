---
title: PLESK: Disable open_basedir without Breaking/commenting Your current httpd.conf Basedir lines
description: 
published: true
date: 2021-06-10T18:30:49.827Z
tags: 
editor: markdown
dateCreated: 2021-06-10T17:49:21.720Z
---

# Disable open_basedir in plesk without breaking/commenting your current httpd.conf basedir lines

Just do following procedure

```
Create a new file, called vhost.conf
This file will include anything you want to disable from httpd.conf main config from your virtual host.
  
# touch /var/www/vhosts/yourdomain.com/conf/vhost.conf
Now we edit the file and we add the following,
  
# vi /var/www/vhosts/yourdomain.com/conf/vhost.conf
Code:
  
<Directory /var/www/vhosts/yourdomain.com/httpdocs> php_admin_value open_basedir none </Directory>
  
Once you finish adding the mentioned lines, its time to reconfigure and restart the webserver config.
  
# /usr/local/psa/admin/sbin/websrvmng -v -a
```