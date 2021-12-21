---
title: PHP Installation
description: 
published: true
date: 2021-12-21T17:14:45.313Z
tags: 
editor: markdown
dateCreated: 2021-12-21T17:14:45.313Z
---

# PHP Installation


PHP is a general-purpose scripting language suited for Web development. This section explains how to install and configure PHP5 in Ubuntu System with Apache2 and MySQL.

This section assumes you have installed and configured Apache 2 Web Server and MySQL Database Server. You can refer tutorial links Apache 2 and MySQL to install and configure Apache 2 and MySQL respectively.

## Installing and configuring PHP in Ubuntu


**Installation**

To install PHP5 you can enter the following command in the server terminal prompt.

```
apt-get install php5 libapache2-mod-php5
```

To run PHP5 scripts from command line you should install php5-cli package. To install php5-cli you can enter the following command.

```
apt-get install php5-cli
```
You can also execute PHP5 scripts without installing PHP5 Apache module. To accomplish this, you should install php5-cgi package.

To use MySQL with PHP5 you should install php5-mysql package. To install php5-mysql you can enter the following command.

```
apt-get install php5-mysql
```

Similarly, to use PostgreSQL with PHP5 you should install php5-pgsql package.

```
apt-get install php5-pgsql
```

**Configuration**

Now you can run PHP5 scripts from your web browser. If you have installed php5-cli package, then you can run PHP5 scripts from your command prompt using command php

By default, the Apache 2 Web server is configured to run PHP5 scripts. In other words, the PHP5 module is enabled in Apache2 Web server automatically when you install the module.

Please verify if the files /etc/apache2/mods-enabled/php5.conf and /etc/apache2/mods-enabled/php5.load exist. If they do not exists, you can enable the module using following command

```
a2enmod php5
```
Once you install PHP5 related packages and enabled PHP5 Apache 2 module, you should restart Apache2 Web server to run PHP5 scripts. You can run the following command at a terminal prompt to restart your web server:

```
/etc/init.d/apache2 restart
```

**Testing**

To verify your installation, you can run following PHP5 phpinfo script:

```
<? phpinfo(); ?>
```

You can save the content in a file phpinfo.php and place it under DocumentRoot directory of Apache2 Web server. When point your browser to http://hostname/phpinfo.php, it would display values of various PHP5 configuration parameters.

## Installing and configuring PHP in CentOS


**Installation**

To install PHP5 you can enter the following command in the server terminal prompt.

For basic PHP

```
yum install php 
```

PHP with all modules

```
yum install php*
```

PHP with custom modules

```
yum install php php-mysql php-mbstring php-gd
```

**Configuration**

In centos I'll configure automatically.

By default system will create php.conf file in the apache conf.d (/etc/httpd/conf.d) directory and load it httpd.conf using Include

```
# Load config files from the config directory "/etc/httpd/conf.d".
#
Include conf.d/*.conf
```

But some its need to configure manually. Then you can follow the procedure.

Add these directives are in /etc/httpd/conf/httpd.conf (if already there, verify they are correct):

```
# Make sure there's only **1** line for each of these 2 directives:

# Use for PHP 5.x:
LoadModule php5_module modules/libphp5.so
AddHandler php5-script .php

# Add index.php to your DirectoryIndex line:
DirectoryIndex index.html index.php

AddType text/html .php

# PHP Syntax Coloring
# (optional but useful for reading PHP source for debugging):
AddType application/x-httpd-php-source phps
```

**Testing**

Create a info.php file in the document root and load it browser.

Create info.php file with the following text

```
<?php
phpinfo();
?>
```

## Installation and Configuration of PHP on  W2k8

Download the latest zipped distribution of PHP from http://php.net. Unzip it. The recommendation is to put all the PHP stuff in a folder just off of the root drive (avoid whitespace), like C:\PHP.

In your PHP directory, you'll find a couple of php.ini-* files. They are pre-configured settings for a PHP install that you can use as an initial setup. The php.ini-recommended is the most secure, hence, the recommended one; just rename it to php.ini and copy to your Windows directory.

This is optional, but recommended step. PHP does not need sessions, but it's something that will most likely be useful.

Create a session directory somewhere on the server. I created C:\PHP\sessionFolder. This directory will hold many small files with session variable information for PHP.

Now change the value of the session.save_path variable in php.ini to be the full path to that directory (session.save_path=C:\PHP\sessionFolder).

You need to point PHP to the directory that holds the extension libraries and you need to uncomment the desired extensions.

- Point PHP to the correct directory:
Set extension_dir in php.ini to "C:\PHP\ext" (extension_dir = "C:\PHP\ext")
- Uncomment the ones you want to use.
It’s important to be sure that php_mysql.dll extension is uncommented (for PHP 5 or newer).

You should add "C:\PHP" to the server's PATH environment variable:

- Right-click on My Computer, choose Properties
- Flip to the Advanced tab
- Click the Environment Variables button
- Double-click the Path variable in the list of System variables.
- Either add "C:\PHP;" to the beginning or ";C:\PHP" to the end (sans quotes, not both).
- Restart IIS for it to take effect.

(To restart IIS you should right-click the local computer in the left pane of IIS Manager, click on All Tasks -> Restart IIS... -> OK)

Instead, you can copy all non-php dll files from C:\PHP to C:\Windows\System32 (or somewhere else in the server's PATH), but the first is the preferred method since it keeps the installation in one place, making upgrading or uninstalling easier.

For these steps, open IIS Manager
(Start -> Control Panel -> Administrative Tools -> Internet Information Services (IIS)  Manager).

Then add new extension (.php)

- Expand the local computer in the left pane
- Right-click on "Web Sites" in the left pane, then click "Properties" in the menu that pops up
- Flip top the Home Directory tab
- Click "Configuration"
- Flip to the Mappings tab
- Click Add...
- Enter the full path to php5isapi.dll in the "Executable" textbox (Browse... to find it more easily if you need to)
- Enter ".php" in the Extension textbox
- Select radial button Limit to, enter "GET,POST,HEAD"
- Click OK all the way out

This will apply to every website.

This sets up IIS to actually respond to requests for php files. Until now, IIS hadn't known what to do with php files, you just told it to pass them through php5isapi.dll.





