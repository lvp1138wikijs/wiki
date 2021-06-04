---
title: Apache Installation
description: 
published: true
date: 2021-06-04T20:37:33.903Z
tags: 
editor: markdown
dateCreated: 2021-06-04T20:37:33.903Z
---


## Installation
Configuration Files of Apache2 
Installation Procedure for CentOS
Installation
Configuration
Apache / php Modules Installations


Apache is the most commonly used Web Server on Linux systems. Web Servers are used to serve Web Pages requested by client computers.

# Installation Procedure for Ubuntu

## Installation

Login to the terminal prompt enter the following command

```
apt-get install apache2
```

## Configuration Files of Apache2 

The apache2 configuration files and folders are located in /etc/apache2/

- apache2.conf : the main Apache2 configuration file. Contains settings that are global to Apache2.
- conf.d : contains configuration files which apply globally to Apache2.
- envvars : file where Apache2 environment variables are set.
- httpd.conf : historically the main Apache2 configuration file, named after the httpd daemon. The file can be used for user specific configuration options that globally effect Apache2.
- ports.conf : houses the directives that determine which TCP ports Apache2 is listening on.
- mods-available : this directory contains configuration files to both load modules and configure them.
- mods-enabled : holds symlinks to the files in /etc/apache2/mods-available. When a module configuration file is symlinked it will be enabled the next time apache2 is restarted.
- sites-available : this directory has configuration files for Apache2 Virtual Hosts. Virtual Hosts allow Apache2 to be configured for multiple sites that have separate configurations.
- sites-enabled : like mods-enabled, sites-enabled contains symlinks to the /etc/apache2/sites-available directory.

If you wish to configure a new virtual host or site, copy that file into the same directory with a name you choose. For example:

```
cp /etc/apache2/sites-available/default /etc/apache2/sites-available/mynewsite
```

Edit the new file mynewsite to configure the new site using your website details.

After your modfication, then enabe the website using following commands

```
a2ensite mynewsite
```

Then restart apache service

```
/etc/init.d/apache2 restart
```

Reference: https://help.ubuntu.com/10.04/serverguide/httpd.html

## Installation Procedure for CentOS

**Installation**

Login to the terminal prompt enter the following command

```
yum install httpd mod_ssl

```

Now configure your system to start Apache at boot time...

```
chkconfig --levels 235 httpd on
```

Then start Apache:

```
/etc/init.d/httpd start
```

**Configuration**

The default location of apache configuration file and folders is /etc/httpd/.

The main configuration file of apache is httpd.conf which is located in /etc/httpd/conf. We have to modify httpd.conf to configure apache.

Open httpd.conf with your favorite editor and configure virtualhost for your website. Check this tutorial more about configuration file and tweak apache.

Example

```
<VirtualHost 64.235.39.114:80>
ServerAdmin webmaster@yourwebsite.com
DocumentRoot /var/www/vhost/yourwebsite.com
ServerName yourwebsite.com
ServerAlias www.yourwebsite.com
ErrorLog logs/yourwebsite.com-error_log
CustomLog logs/yourwebsite.com-access_log common
</VirtualHost>
```

ServerAdmin: Your address, where problems with the server should be e-mailed.

DocumentRoot: The directory out of which you will serve your documents.

ServerName: Name of your website

ServerAlias:  directive sets the alternate names for your website

After you modify the settings and then restart apache,

```
/etc/init.d/httpd restart
```

Reference: http://httpd.apache.org/docs/2.2/vhosts/name-based.html

