---
title: Issues with Fastcgi
description: 
published: true
date: 2021-06-10T18:29:51.998Z
tags: 
editor: markdown
dateCreated: 2021-06-10T17:45:36.385Z
---

Take a backup of apache, php configuration files * Go to the public_html directory of the user and in .htaccess add the following line:

- AddHandler php5-fastcgi .php
  Action php5-fastcgi /cgi-bin/php5.fcgi
  
Go to the cgi-bin folder within your accounts public_html folder and add two files.
- First one is the copy of your php.ini with your modifications
- The second file name php5.fcgi and add the following lines in it:  

```
#!/bin/sh

export PHP_FCGI_CHILDREN=1
export PHP_FCGI_MAX_REQUESTS=10
exec /usr/local/cpanel/cgi-sys/php5
```
Go to usr/local/apache/conf/php.conf and put the following lines in that file:

```
LoadModule fcgid_module modules/mod_fcgid.so
MaxRequestsPerProcess 500
MaxProcessCount 1000
DefaultMaxClassProcessCount 100
IPCConnectTimeout 60
IPCCommTimeout 60
PHP_Fix_Pathinfo_Enable 1
IdleTimeout 900
IdleScanInterval 120
BusyTimeout 300
BusyScanInterval 120
ErrorScanInterval 9
ZombieScanInterval 9
ProcessLifeTime 3600

AddHandler php5-fastcgi .php
Action php5-fastcgi /cgi-bin/php5.fcgi
AddType application/x-httpd-php .php
```

Restart apache.

