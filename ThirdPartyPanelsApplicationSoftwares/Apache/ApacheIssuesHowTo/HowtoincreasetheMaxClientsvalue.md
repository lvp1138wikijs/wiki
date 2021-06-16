---
title: How to increase the MaxClients value greater than the current HARD_SERVER_LIMIT set for Apache
description: 
published: true
date: 2021-06-16T18:01:31.111Z
tags: 
editor: markdown
dateCreated: 2021-06-16T18:01:31.111Z
---

In order to increase the MaxClients value greater than the current HARD_SERVER_LIMIT set for Apache, please do the following steps:

1) Check if there is any hard server limit specified for Apache max connections using the following command.

```
/usr/local/apache/bin/httpd -V | grep HARD_SERVER_LIMIT
```
2) If it is there, then you would need to look for this directive in the Apache's header file /usr/local/apache/include/httpd.h.

3) Edit the file using the vi editor and increase the HARD_SERVER_LIMIT as per your requirement.

4) Recompile Apache using /scripts/easyapache

5) There you will have an option to increase the Apache HARD_SERVER_LIMIT, since easyapache looks for the header files and sees the new value while build. By default the MaxClients value will be 256.

6) Once the build completes, you can see the new HARD_SERVER_LIMIT.


