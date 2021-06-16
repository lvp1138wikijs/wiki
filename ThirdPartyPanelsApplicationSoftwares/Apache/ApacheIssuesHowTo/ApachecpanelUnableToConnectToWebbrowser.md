---
title: Apache/cpanel:Unable To Connect To Webbrowser
description: 
published: true
date: 2021-06-16T16:29:42.053Z
tags: 
editor: markdown
dateCreated: 2021-06-16T16:29:42.053Z
---

Sample Ticket :CZX-371-99286

If the customer complains that he cannot obtain his websites on the browser, you may check the status of the apache server.

```
root@vps [~]# service httpd status

Looking up localhost
Making HTTP connection to localhost
Alert!: Unable to connect to remote host.

lynx: Can't access startfile http://localhost/whm-server-status
root@vps [~]#
```

To solve this issue kill the semaphore processes.

```
ipcs -s | grep nobody | perl -e ‘while (<STDIN>) { @a=split(/\s+/); print `ipcrm sem $a[1]`}’
```
Finally restart apache

```
service apache restart
```



