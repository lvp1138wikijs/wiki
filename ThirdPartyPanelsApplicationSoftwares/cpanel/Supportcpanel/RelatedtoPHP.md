---
title: Related to PHP
description: 
published: true
date: 2021-12-27T18:58:12.847Z
tags: 
editor: markdown
dateCreated: 2021-12-27T18:55:00.181Z
---

# Related to PHP

**Upgrading PHP version to 5**

Before you upgrade the PHP version , make sure that you will either note or memorize the modules that were enabled in previous php version and once the upgrades done

you will have to enable those php modules again before it starts throwing out the error.

- Login  to the server SSH as root 
- Use /scripts/upcp – force
- this can take a while. 
- Use /script/easyapache

Once you used the above command , it will show the options screen ( You can do the php version upgrade from WHM easyapache too )
 
SELECT OPTION 7

- Select ―Php Module —>‖
- Uncheck current PHP version 
- Check latest version of PHP5
- Select ―Exit‖
- Select ―Exit‖ again
- Sit back and wait, it can take 10-60 minutes to complete

## Ioncube Loader Error while browsing the website

Some times with a website that is build in PHP may face

Site error: the file  /home/USER/public_html/index.php requires the ionCube PHP Loader ioncube_loader_lin_X.X.so to be installed

To Resolve this issue

Create a ‗php.ini‘ within the following:
 
zend_extension  =  /home/USER/public_html/ioncube/ioncube_loader_lin_4.X.so  ( Remember its customized php ini )(Correct the URL with replacing with the latest version )

Download from : http://www.ioncube.com/loaders.php  Replace USER with the username of the account you are uploading the php.ini file to.
Replace ―X‖ with the appropriate version of the ioncube loader 
 Upload the php.ini to  your public_html directory.If you are running your script from a  directory other than public_html - for  example /home/USER/public_html/blog/index.php you will need to upload the php.ini file to that directory

## How to Enable errors logging for PHP

PHP errors are by default logged to the cpanel server‘s error log file. But it is also possible to instead log PHP errors to a file of your choice.
If you do not currently have a php.ini, make one and place it in the same folder(s) as the PHP script(s) that you want to track errors for.
You will need to add the following 2 lines:
log_errors = On 
error_log = error_log
You can either ON the above mentioned options in server's default php.ini which is located at /usr/local/lib/php.ini

## Cpanel/WHM ways to configure PHP

Cpanel/WHM ways to configure PHP

 

**DSO**

Provides PHP through libphp4.so or libphp5.so (aka, mod_php).

This option is usually the fastest way to execute PHP requests; however, this option uses the system user called

nobody to serve all PHP requests.

 

**suPHP**

Provides PHP through mod_suphp. Using this option is probably the most flexible way of serving PHP requests and is generally very secure. Under this option, PHP scripts will be executed by the user who owns the VirtualHost serving the request.

 

**FCGI**

This option serves PHP through mod_fcgid. This is a fast way of serving PHP requests but will most likely require that you tweak php.conf. You can enable suEXEC to execute PHP scripts under the user who owns the VirtualHost that is serving the request or, if suEXEC is disabled, PHP will be served by the system user ‗nobody‘.

 
##  Run PHP as user instead of as the web server user nobody.

suPHP is a tool for executing PHP scripts with the permissions of their owners.It consists of an Apache module (mod_suphp) and a setuid root binary (suphp) that is called by the Apache module to change the uid of the process executing the PHP interpreter.

You can run PHP as the user (like CGI scripts do with Apache‘s suEXEC), with Easy Apache‘s PHP As User option.

This will enable suPHP, greatly improving the permissions situation.Vulnerable scripts will be limited to the user in question, and are less likely to affect other users. It also changes howPHP interacts with Apache; for example, directives like php_$value are not valid for mod_suphp.mod_suphp is considerably slower than mod_php.

PHP runs as part of the web server so that, among other things, certain tasks can be done once and held in memory

instead of repeated with each request. This helps to speed the server‘s performance, and requires that PHP run as the web server‘s user nobody.

 Since that is the case, PHP and directory permissions generally need to be very loose, so PHP can manipulate things.

This can allow any user to employ a PHP script to read and write other users‘ data. At times, a flaw in PHP can evenallow a PHP script to gain root access or take over data in requests on other users‘ PHP scripts.

## Apache PHP Request Handling in Cpanel 

Cpanel PHP‘s main configuration file is located at /usr/local/apache/conf/php.conf

 The php.conf file is called by the Apache configuration file (httpd.conf) by means of an include command.

WHM provides an interface that can assist you in configuring PHP. It is located in Service Configuration >> ApacheConfiguration >> PHP and SuExec Configuration. You are also able to access a command line interface that provides the same options through the following script:

/usr/local/cpanel/bin/rebuild_phpconf

## Custom php.ini not working on SuExec Enabled Server

Normally, on SuExec Enabled Server, you can create php.ini in your account to customize php settings for your account. If php.ini is created under an account with customize php setting and it doesn’t work for you, then this is because override is disabled in /opt/suphp/etc/suphp.conf

Quote:

```
[phprc_paths]
;Uncommenting these will force all requests to that handler to use the php.ini
;in the specified directory regardless of suPHP_ConfigPath settings.
application/x-httpd-php=/usr/local/lib/
application/x-httpd-php4=/usr/local/php4/lib/
application/x-httpd-php5=/usr/local/lib/
```

This forces suphp to use the php.ini from /usr/local/lib/
You can comment these lines and then restart Apache to resolve the issue.

Quote:
[phprc_paths]
;Uncommenting these will force all requests to that handler to use the php.ini
;in the specified directory regardless of suPHP_ConfigPath settings.
;application/x-httpd-php=/usr/local/lib/
;application/x-httpd-php4=/usr/local/php4/lib/
;application/x-httpd-php5=/usr/local/lib/

Done