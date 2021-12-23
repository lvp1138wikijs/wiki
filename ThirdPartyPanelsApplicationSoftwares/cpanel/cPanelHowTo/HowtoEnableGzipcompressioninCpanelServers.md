---
title: How to Enable Gzip compression in Cpanel Servers
description: 
published: true
date: 2021-12-23T19:32:16.274Z
tags: 
editor: markdown
dateCreated: 2021-12-23T19:32:16.274Z
---

# How to Enable Gzip compression in Cpanel Servers


In order to enable gzip for "Website optimization" in cPanel, Please do the following steps:

1. check if mod_deflate is there using the following commands:

```
# httpd -l | grep deflate
  mod_deflate.c
```

2. If not, you will need to recompile Apache with that module enabled.

3. Once completed, log into the user account and under software/services, click on website optimization:enable compression for the site.

4. For web Page Content Compression Verification test, please use the site http://www.whatsmyip.org/http-compression-test/ .

5. If the above does not work, then most probably compression is already enabled in the .htaccess file for certain files and the cPanel is not overwriting it.

6. You can Enable gzip in the .htaccess file by adding the following lines:

```
#Gzip
<ifmodule mod_deflate.c>
AddOutputFilterByType DEFLATE text/text text/html text/plain text/xml text/css application/x-javascript application/javascript text/javascript
</ifmodule>
#End Gzip
```

