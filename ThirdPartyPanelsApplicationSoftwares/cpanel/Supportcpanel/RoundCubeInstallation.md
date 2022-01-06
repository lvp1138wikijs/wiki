---
title: Round Cube Installation
description: 
published: true
date: 2022-01-06T05:01:57.907Z
tags: 
editor: markdown
dateCreated: 2022-01-06T05:01:57.907Z
---

# Round Cube Installation

In order to install round cube in cpanel server, please do the following steps:

Remove the previous traces of Roundcube in the server.

```
cd /usr/local/cpanel/base

rm -rf roundcube*

mysql

1. mysql>drop database roundcube;
```

**Note**:Before starting the installation, you need to know the root password of Mysql.

```
cd /usr/local/cpanel/base
wget http://easynews.dl.sourceforge.net/sourceforge/roundcubemail/roundcubemail-0.1beta2.1.tar.gz
tar -zxvf roundcubemail-0.1beta2.1.tar.gz
mv -f roundcubemail-0.1beta2 roundcube
cd roundcube
chmod -R 777 temp
chmod -R 777 logs
```

**Create the database**. Find mysql root password from /root/.my.cnf.

Login as user, root and do the following commands.

```
mysql -u root -p

Password:

mysql>CREATE DATABASE roundcube;

mysql>use roundcube;

mysql >grant all on roundcude.* to roundcube@localhost identified by "password";

mysql>source SQL/mysql.initial.sql;

mysql>quit
```

**Add the configuration**:

```
cd config

mv db.inc.php.dist db.inc.php

mv main.inc.php.dist main.inc.php
```

**Edit the configuration files**

**Open db.inc.php configuration file using vi editor, and make the changes as follows**:

```
find the line "$rcmail_config[’db_dsnw’] = ‘mysql://root:rootpass@localhost/roundcube’; " and replace it to "$rcmail_config[’db_dsnw’] = ‘mysql://roundcube:pass@localhost/roundcubemail’;"
```

Specify the database username and password you specified when you created the database from mysql command.

Open main.inc.php using vi editor, and make the changes as follows:

```
find the line "$rcmail_config[’default_host’] = ”;" and replace it to "$rcmail_config[’default_host’] = ‘localhost’;"
```

**Configure cPanel to show roundcube in the theme**.

```
cd /usr/local/cpanel/base/roundcube/skins/default/images/
cp roundcube_logo.png /usr/local/cpanel/base/frontend/x/images/roundcube_logo.png
cp roundcube_logo.png /usr/local/cpanel/base/webmail/x/images/roundcube_logo.png
wget http://www.yourserverguide.com/Files/HGpatch-roundcube-1.0BETA2.1
patch -p0 < HGpatch-roundcube-1.0BETA2.1
```

If you receive a message stating: Reversed (or previously applied) patch detected! Assume -R? Please press N for No as this is because you previously installed roundcube.

This will auto do all the necessary changes to round cube and the X theme. Once the patch is executed you may now access round cube via http://yourdomain/webmail