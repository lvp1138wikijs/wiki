---
title: CSF - Resolve Excessive resource usage Warning Mail
description: 
published: true
date: 2021-12-27T15:06:40.410Z
tags: 
editor: markdown
dateCreated: 2021-12-27T15:06:40.410Z
---

# CSF - Resolve Excessive resource usage Warning Mail

**Problem**
Received warning emails

```
Subject: lfd on cp.worldoflcd.com: Excessive resource usage: encoreel (9267 (Parent PID:7398))
Time:         Sun Mar  9 20:45:20 2014 +0800
Account:      encoreel
Resource:     Virtual Memory Size
Exceeded:     253 > 200 (MB)
Executable:   /usr/bin/php
Command Line: /usr/bin/php /home/encoreel/public_html/index.php
PID:          9267 (Parent PID:7398)
Killed:       No
```

The email are from CSF firewall monitoring system. It has set Vitual memory usage limit to 200 per user

**Solution**

Increase the limit from WHM

 

To increase the limit please go to WHM >> Plugins » ConfigServer Security & Firewall.

 

Click on Firewall Configuration under csf - ConfigServer Firewall

 

Under **Process Tracking** >> Increase the value of **PT_USERMEM**