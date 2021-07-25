---
title: Stop Open Relay of Exim
description: 
published: true
date: 2021-07-25T00:03:02.606Z
tags: 
editor: markdown
dateCreated: 2021-07-25T00:03:02.606Z
---

# Stop Open Relay of Exim

To stop open relay please do the following commands

```
/scripts/fixrelayd
 
/etc/init.d/antirelayd restart
 
service exim restart
```