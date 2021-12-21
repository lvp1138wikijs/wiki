---
title: PHP pages are downloading instead of loading in Browser
description: 
published: true
date: 2021-12-21T17:17:04.852Z
tags: 
editor: markdown
dateCreated: 2021-12-21T17:17:04.852Z
---

# PHP pages are downloading instead of loading in Browser


**Issue** :


```
The browser is giving the option to download php page (index.php) instead of loading it. 
Control Panel :cPanel
```

**Reason** :

```
PHP handler is not configured properly in the server
```

**Solution** :

```
Step 1:  Login to the server and check the current PHP configuration. 
You can check it via WHM or via command line 

WHM : Home >> Service Configuration >> Configure PHP and SuExec
Command Line : /usr/local/cpanel/bin/rebuild_phpconf --current
Sample Result:
--------------
root@ns1 [/home/cafetg/public_html]# /usr/local/cpanel/bin/rebuild_phpconf --current
Available handlers: suphp dso fcgi cgi none
DEFAULT PHP: 5
PHP4 SAPI: none
PHP5 SAPI: none
SUEXEC: enabled
RUID2: not installed 
--------------
```

```
Step 2 (a): 

If PHP handler is not there, the value will be "none" (as shown above).
Then, add proper handler (suPHP, DSO, FCGI etc) and this will fix the issue. 
You can add it from WHM : Home >> Service Configuration >> Configure PHP and SuExec
 
Step 2 (b):
If PHP handler is already there, but still issue persists, add the following into ".htaccess" file of the domain.
-----------
AddHandler application/x-httpd-php5 .php .php4 .php3 .html
AddType application/x-httpd-php5 .html
-----------
Restart apache and check.
```

Reference Ticket# RRL-445-61307


