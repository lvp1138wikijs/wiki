---
title: Steps to find Spam Account in Linux server with Plesk
description: 
published: true
date: 2021-07-18T05:13:02.840Z
tags: 
editor: markdown
dateCreated: 2021-07-18T05:13:02.840Z
---

# Steps to find Spam Account in Linux server with Plesk


**If a customer ask you to find which email account is spamming, use following procedure to find it from Plesk server**:

```
1) Login to Plesk control panel.

2) Click Settings > Mail Server

3) Click on Mail Queue

4) Open a spam email.

5) Check the sending IP address

6) Now login to the server via SSH.

7) cd /usr/local/psa/var/log

8) cat maillog | grep "IP address"
```

**For example**:

```
root@anchorfabrication log]# cat maillog | grep "213.171.204.130"

Aug  4 01:13:44 anchorfabrication smtp_auth: SMTP user test@businelle.com : logged in from server1.advanced-ref.co.uk [213.171.204.130]
```

Refer ticket # BQE-308-51074

