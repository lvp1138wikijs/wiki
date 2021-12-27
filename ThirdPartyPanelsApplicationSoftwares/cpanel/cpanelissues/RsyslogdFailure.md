---
title: Rsyslogd Failure
description: 
published: true
date: 2021-12-27T16:04:43.087Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:04:43.087Z
---

# Rsyslogd Failure


This error message occurs  when you have set two daemons for logging errors.

You may encounter this error.

When you restart services from WHM  i.e,  WHM -> Service Configuration -> Service Manager, you may see this error.

```
Waiting for rsyslogd to restart………………………………………………………finished. 
rsyslogd has failed, please contact the sysadmin (result was “rsyslog is not running”).
```

**Solution**:

When you have two daemons for logging i.e.,  syslogd and rsyslogd this error occurs. The error can be solved by setting just one logging daemon under service manager.