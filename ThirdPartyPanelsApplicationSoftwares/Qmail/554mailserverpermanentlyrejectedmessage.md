---
title: 554 mail server permanently rejected message
description: 
published: true
date: 2021-07-24T05:20:54.471Z
tags: 
editor: markdown
dateCreated: 2021-07-24T05:20:54.470Z
---

# 554 mail server permanently rejected message

Fixing 554 mail server permanently rejected message (#5.3.0) Errors


> Qmail Error!.. 
> 554 mail server permanently rejected message (#5.3.0) Errors… 
{.is-danger}

This error can be because of plesk updater that had updated an unsupported version.

This problem can be fixed by reinstalling Dr. Web.

1. Login to your server as root
1. Search for Dr. Web antirus using command
    - rpm -qa | grep dr
1. It should give you result like

```
drweb-4.32.2-rh7_psa
drweb-qmail-4.32-rhel4.build75050824.12
```
4. Remove them using rpm command
   - rpm -e filename
   
```
 rpm -e drweb-4.32.2-rh7_psa
rpm -e  drweb-qmail-4.32-rhel4.build75050824.12
```

5. Login to plesk using admin login
6. Go to plesk updater
7. Select Dr. Web by ticking on box and click on install
8. Check /etc/drweb/drweb32.ini and make sure all settings are correct
9. Start Dr. Web from service management.
