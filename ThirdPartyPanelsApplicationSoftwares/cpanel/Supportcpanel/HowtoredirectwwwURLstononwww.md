---
title: How to redirect www URLs to non-www / non-www to www
description: 
published: true
date: 2021-12-27T19:59:43.368Z
tags: 
editor: markdown
dateCreated: 2021-12-27T19:59:43.368Z
---

# How to redirect www URLs to non-www / non-www to www


**Redirect www URLs to non-www**

To do this write the following lines at the beginning of  the .htaccess file in the public_html folder:

```
RewriteEngine On
RewriteCond %{HTTP_HOST} ^www.yourdomain.com [NC]
RewriteRule ^(.*)$ http://yourdomain.com/$1 [L,R=301]
```

From now on, when someone accesses http://www.yourdomain.com  will be redirected to http://yourdomain.com.

**Redirect non-www to www**
To do this write the following lines at the beginning of  the .htaccess file in the public_html folder:

```
RewriteEngine On
RewriteCond %{HTTP_HOST} ^yourdomain.com [NC]
RewriteRule ^(.*)$ http://www.yourdomain.com/$1 [L,R=301]
```

From now on, when someone accesses http://yourdomain.com will be redirected to http://www.yourdomain.com.



