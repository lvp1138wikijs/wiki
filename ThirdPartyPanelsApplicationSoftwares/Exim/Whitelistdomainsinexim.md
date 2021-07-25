---
title: Whitelist domains in exim
description: 
published: true
date: 2021-07-25T03:39:37.957Z
tags: 
editor: markdown
dateCreated: 2021-07-25T03:39:37.957Z
---

# Whitelist domains in exim

- Login to the server SSHas root. Make a sender whitelist file.

```
touch /etc/exim_whitelist_senders
```

- Take a backup of the exim conf and open it.

```
cp -p /etc/exim.conf /etc/exim.conf.BKP
vi /etc/exim.conf
```

- Add the line on top of the file

```
addresslist whitelist_senders = wildlsearch;/etc/exim_whitelist_senders
 
Now search for the line
require verify = sender/callout
 
Comment that line and add the following below that.
 
!verify = sender/callout=30s,defer_ok,maxwait=60s
!senders = +whitelist_senders
```

- Save conf file.
- Add email address to the /etc/exim_whitelist_senders file one by one. Wildcard is also acceptable here, Eg: *@domain.com
- Restart exim