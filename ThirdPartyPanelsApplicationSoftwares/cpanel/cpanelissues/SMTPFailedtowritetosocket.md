---
title: SMTP: Failed to write to socket: not connected (code: -1, response: )
description: 
published: true
date: 2021-12-27T16:13:36.168Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:13:36.168Z
---

# SMTP: Failed to write to socket: not connected (code: -1, response: )


Sometimes while sending email from Horde, it takes long time to load and at the end it shows the error message given below.

```
Horde error :Failed to set sender: user@emailaddress.com [SMTP: Failed to write to socket: not connected (code: -1, response: )]
```

Given below are the two parameters in CSF configuration file (/etc/csf/csf.conf) that should be checked.

1. Ensure that “SMTP_ALLOWLOCAL” is enabled in CSF configuration file. It should be enabled if you want to allow local connections to port 25 on the server (e.g. for webmail or web scripts).

```
SMTP_ALLOWLOCAL = “1?
```

2. Ensure that “SMTP_ALLOWLOCAL” has the value “1″.

If these options are not enabled, enable them and restart CSF using the command given below.

```
/etc/init.d/csf restart
```