---
title: Error while adding subdomain
description: 
published: true
date: 2021-12-27T15:16:17.041Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:16:17.041Z
---

# Error while adding subdomain


When you get an error like "**Error from domain wrapper: domain.com is owned by another user**." while adding sub domain in cpanel, then please do the following steps:

This happens when cPanel doesn’t remove the subdomain correctly and when you add it(if you are trying to delete the subdomain and then adding it), cpanel thinks it’s still there. So when you try to add it back you get an error.Now here goes the fix:

```
1. Remove domain.com from /var/cpanel/users/cpanel-username

2. Run /scripts/updateuserdomains as root user on the server.

3. Remove /var/named/domain.com.db if the file exists (it doesn’t always)

4. Remove the virtualhost for domain.com on /usr/local/apache/conf/httpd.conf

5. Remove domain.com from /etc/named.conf
```

Now you can add the domain back on in cPanel with no problems.

