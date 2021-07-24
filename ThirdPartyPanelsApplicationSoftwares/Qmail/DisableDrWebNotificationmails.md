---
title: Disable Dr.Web Notification mails
description: 
published: true
date: 2021-07-24T05:23:12.188Z
tags: 
editor: markdown
dateCreated: 2021-07-24T05:23:12.188Z
---

# Disable Dr.Web Notification mails


**Solution**:
**Disable Cron Summery Notifications**

Set CronSummary to 'No' in section [Updater] in /etc/drweb/drweb32.ini.

vi /etc/drweb/drweb32.ini and search for cron summery and set it to no

```
CronSummary = no
```

Then just restart Dr. Web with:

/etc/init.d/drwebd restart

**Disable Virus Scan Notifications**

You can edit /etc/drweb/drweb_handler.conf to eliminate receiving notification messages when Dr. Web has an issue:

```
[VirusNotifications]

SenderNotify = no

AdminNotify = no

RcptsNotify = no
```
Then just restart Dr. Web with: /etc/init.d/drwebd restart

