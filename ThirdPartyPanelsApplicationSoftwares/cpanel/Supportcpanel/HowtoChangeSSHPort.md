---
title: How to Change SSH Port
description: 
published: true
date: 2021-12-27T19:48:34.445Z
tags: 
editor: markdown
dateCreated: 2021-12-27T19:48:34.445Z
---

# How to Change SSH Port

Change SSH Port
1.Login to server via SSH as root user

2. Open SSH configuration file sshd_config in your favorite editor 

```
vi /etc/ssh/sshd_config
```

3. Find the line

```
#Port 22
```
4.  Uncomment it (Remove #) and change it to look like

```
Port 3223
```
5. Then save and restart ssh service.

```
/etc/init.d/sshd restart
```




