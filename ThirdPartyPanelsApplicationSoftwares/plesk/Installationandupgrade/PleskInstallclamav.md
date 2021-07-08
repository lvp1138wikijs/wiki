---
title: Plesk:Install clamav
description: 
published: true
date: 2021-07-08T00:01:41.296Z
tags: 
editor: markdown
dateCreated: 2021-07-08T00:01:41.296Z
---

# Plesk:Install clamav

- First login to your server vis SSH
- First remove drweb

```
Yum remove drweb

yum remove drweb-qmail
```

- Install clamav with the following commands

```
yum install qmail-scanner 

yum install clamd" 

yum install spamassassin

/usr/bin/qmail-scanner-reconfigure
```