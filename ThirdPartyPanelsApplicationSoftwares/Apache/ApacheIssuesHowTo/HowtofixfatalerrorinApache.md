---
title: How to fix fatal error in Apache
description: 
published: true
date: 2021-06-16T17:59:00.488Z
tags: 
editor: markdown
dateCreated: 2021-06-16T17:59:00.488Z
---

If PHP scripts are giving 500 Internal Server Errors and apache error logs shows the following error, please try it out the following fix.

```
FATAL:  erealloc():  Unable to allocate 37581 bytes

[Mon Apr 14 19:07:39 2008] [error] [client 125.17.242.245] Premature end

 of script headers: /home/username/public_html/site/index.php
```

**SOLUTION**:

The cause of the problem is because of the line "RLimitMEM 22369621" in httpd.conf file. In order to fix this error, just commented out the line using the following command:

```
grep RLimitMEM /usr/local/apache/conf/httpd.conf#RLimitMEM
```

Then restart the httpd service.

