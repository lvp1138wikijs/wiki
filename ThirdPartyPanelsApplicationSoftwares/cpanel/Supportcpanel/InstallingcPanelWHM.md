---
title: Installing cPanel/WHM
description: 
published: true
date: 2021-12-29T21:13:26.183Z
tags: 
editor: markdown
dateCreated: 2021-12-29T21:13:26.183Z
---

# Installing cPanel/WHM

**Procedure ONLY for DEDICATED Server. Colossus customer can select cPanel while requesting VM from their client portal**

**Preinstallation steps**

Change hostname of server to something valid like cp.serverpoint.com, you can change it in following 2 files

In centos

- /etc/hosts
- /etc/sysconfig/network

**Installation**

Login to server via ssh using root login

```
# cd /home
# wget http://layer1.cpanel.net/latest
# sh latest
```

The installer has now started, and can take between 30 and 60 minutes depending on your machine. If you are asked any questions press the Enter key or q if there is no default.

NOTE: You must be on a stable Internet connection to install cPanel. If your shell session disconnects during the installation of cPanel, the installation will be aborted. You can restart the installation by using sh latest again however, but it is recommend reformatting your machine and starting over, ensuring there are no problems with the installation.

Absolute filesystem path : /home/username


**ISSUE cPanel License:**

Once the installation completed then cPanel team will issue  a temporary license for 15 days on the main IP address.  You can contact Ram / Shabi to issue a permanent license on the customer server main IP. 
