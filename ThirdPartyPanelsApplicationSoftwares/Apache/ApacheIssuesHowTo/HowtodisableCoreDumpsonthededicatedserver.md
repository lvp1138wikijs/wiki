---
title: How to disable Core Dumps on the dedicated server
description: 
published: true
date: 2021-06-16T17:46:55.906Z
tags: 
editor: markdown
dateCreated: 2021-06-16T17:46:55.906Z
---

In order to disable Core Dumps on the dedicated server, please do the following steps:

1. Login to your server as root.

2. Open up /etc/init.d/httpd using vi editor

```
vi /etc/init.d/httpd
```
3. add ulimit -c 0 below ulimit –n

4. Save and exit

5. Restart Apache service.


