---
title:  Change php.ini values in shared hosting
description: 
published: true
date: 2021-04-03T13:27:15.785Z
tags: 
editor: markdown
dateCreated: 2021-04-03T13:27:15.785Z
---

In shared hosting environment, we cannot edit the 'PHP.ini ' file directly. So there is an alternate file which is linked to the php.ini .

----------------------

PHP -i | grep php.ini
/opt/alt/php56/link/conf/alt_php.ini

----------------------

Edit this file to change the PHP values.

Can refer the below article for correct syntax.
https://www.tutorialspoint.com/php/php_ini_configuration.htm

NB: Please do not edit .htaccess to update PHP values. 