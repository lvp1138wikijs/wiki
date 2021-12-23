---
title: How to Change tomcat port in cpanel
description: 
published: true
date: 2021-12-23T19:20:21.205Z
tags: 
editor: markdown
dateCreated: 2021-12-23T19:20:21.205Z
---

# How to Change tomcat port in cpanel


Open /usr/local/jakarta/apache-tomcat-5.5.36/conf/server.xml

```
# nano -w /usr/local/jakarta/apache-tomcat-5.5.36/conf/server.xml
```

Find 8080

and replace it with 80 or any port which customer want.

Save file

Go to WHM, and restart Tomcat from service restart option.