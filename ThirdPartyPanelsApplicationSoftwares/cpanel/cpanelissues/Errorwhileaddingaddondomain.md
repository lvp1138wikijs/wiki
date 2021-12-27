---
title: Error while adding addon domain
description: 
published: true
date: 2021-12-27T15:14:10.000Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:14:10.000Z
---

# Error while adding addon domain


When you get an error like "resolving the error: cpanel is already configured. Sorry, that domain is already setup (remove it from httpd.conf)" while adding addon domain in cpanel, please do the following steps:

1) Log into your account via SSH as root user and run the following commands.

```
grep -r example.com /var/cpanel/userdata
```

2) If the entry for example.com exists in the cache file, then remove the files using following command.

```
rm /var/cpanel/userdata/username/*.cache
```

3) Then edit /var/cpanel/userdata/username/main file using vi editor, and then remove the example.com from it.

4) Then restart the httpd service and you could be easily add the addon domain without any issues.