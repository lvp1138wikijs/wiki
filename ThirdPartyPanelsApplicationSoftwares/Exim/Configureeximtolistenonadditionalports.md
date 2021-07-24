---
title: Configure exim to listen on additional ports.
description: 
published: true
date: 2021-07-24T23:17:44.735Z
tags: 
editor: markdown
dateCreated: 2021-07-24T23:17:44.735Z
---

# Configure exim to listen on additional ports.

Exim is a popular Message Transfer Agent (MTA) used on Unix systems. By default Exim will be listening on port 25. To make Exim listening on other additional port, say 26, please do the following steps.



1) Open the file **/etc/exim.conf** using vi editor and then add the following line.

```
daemon_smtp_ports = 25:198:200
```

2) After this restart Exim using the following commands.

```
service exim restart
or
/etc/init.d/exim restart
```

This will make Exim to listen on ports 25 as well as 26.

