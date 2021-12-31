---
title: How to install Fantastico on cPanel/WHM
description: 
published: true
date: 2021-12-31T18:01:33.586Z
tags: 
editor: markdown
dateCreated: 2021-12-31T18:01:33.586Z
---

# How to install Fantastico on cPanel/WHM


Fantastico is a commercial script library that automates the installation of web applications to a website. Fantastico scripts are executed from the administration area of a website control panel such as cPanel.

Fantastico scripts are usually executed when a new website is created, or a new application is added to an existing website. The scripts typically create tables in a database, install software, adjust permissions, and modify web server configuration files.

1)Login to your server as root through SSH.

2)Then enter the following commands.

```
cd /usr/local/cpanel/whostmgr/docroot/cgi
wget -N http://files.betaservant.com/files/free/fantastico_whm_admin.tgz
tar -xzpf fantastico_whm_admin.tgz
rm -rf fantastico_whm_admin.tgz
```

3)Now go to WHM -> Add-Ons (Plugins on v11.x or higher) -> Fantastico De Luxe WHM Admin (scroll down the left menu) and follow the on screen instructions.

Note: If you get a Source Guardian error when you go to Fantastico for the first time, just run this command:

```
chmod -R 0755 /usr/local/cpanel/3rdparty/etc/ixed
```


