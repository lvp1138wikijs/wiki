---
title: phpMyAdmin Error in Plesk Linux
description: 
published: true
date: 2021-07-11T00:25:05.185Z
tags: 
editor: markdown
dateCreated: 2021-07-11T00:25:05.185Z
---

# phpMyAdmin Error in Plesk Control Panel

Plesk Control Panel is showing an error when accessing Webmin / PhpMyAdmin.

**Error**

> Error
> MySQL Said:
> 
> #1045 - Access denied for user 'psaadm'@'localhost' (using password: NO)
{.is-danger}

**Cause**

Its due to the mismatch between the user login credentials stored in phpMyAdmin configuration and the database.

**Solution**

1. Make sure that the Plesk Panel phpMyAdmin user exists in mysql.user table and having correct password and privileges.
1. Username and password can be found in **/usr/local/psa/admin/htdocs/domains/databases/phpMyAdmin/libraries/config.default.php**
1. You can find the **USER**, **PASSWORD** and **DATABASE**name as follows.

```
#grep controluser /usr/local/psa/admin/htdocs/domains/databases/phpMyAdmin/libraries/config.default.php
Result Should be #  $cfg['Servers'][$i]['controluser'] = $GLOBALS['db_host'] != 'localhost' ? '' : 'User name';
 
#grep controlpass /usr/local/psa/admin/htdocs/domains/databases/phpMyAdmin/libraries/config.default.php
Result Should be #  $cfg['Servers'][$i]['controlpass'] = 'Password';
 
#grep pmadb /usr/local/psa/admin/htdocs/domains/databases/phpMyAdmin/libraries/config.default.php
Result Should be #  $cfg['Servers'][$i]['pmadb'] = $GLOBALS['db_host'] != 'localhost' ? '' : 'Database name'; ......
```

4. Try to login as the **USER** and **PASSWORD**which you get above, into MySQL from the command line.

```
# mysql -uDB_USER -pDB_PASSWORD -D DB_NAME
ERROR 1045 (28000): Access denied for user 'pma_*****'@'localhost' (using password: YES)
```

5. If user doesn't exist in Mysql then create it with commands as,

```
# mysql -uadmin -p`cat /etc/psa/.psa.shadow`
mysql> use mysql
mysql> INSERT INTO `db` VALUES ('localhost','DATABASE','USER','Y','Y','Y','Y','N' ,'N','N','N','N','N','N','N','N','N','N','N','N');
mysql> INSERT INTO `user` VALUES ('localhost','USER',password('PASSWORD'),'N','N',' N','N','N','N','N','N','N','N','N','N','N','N','N' ,'N','N','N','N','N','N','N','N','N','N','N','','' ,'','',0,0,0,0);
mysql> flush privileges;
```

**Note**: Do not forget to replace all **USER**, **PASSWORD** and **DATABASE** with the right values which get from “config.default.php”.



