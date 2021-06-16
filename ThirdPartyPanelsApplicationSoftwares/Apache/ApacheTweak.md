---
title: Apache Tweak
description: 
published: true
date: 2021-06-16T18:09:56.644Z
tags: 
editor: markdown
dateCreated: 2021-06-16T18:09:56.644Z
---

Apache web server can be tweak by modifying default configuration value in the configurations files.

## Change Apache Default Configuration

**Section 1: Global Environment**

The directives in this section affect the overall operation of Apache, such as the number of concurrent requests it can handle or where it can find its configuration files.

**ServerRoot**: The top of the directory tree under which the server's configuration, error, and log files are kept.

ServerRoot "/etc/httpd"

**PidFile**: The file in which the server should record its process identification number when it starts. Note the PIDFILE variable in /etc/sysconfig/httpd must be set appropriately if this location is changed.

PidFile run/httpd.pid

**Timeout**: The number of seconds before receives and sends time out.

Timeout 60

**KeepAlive**: Whether or not to allow persistent connections (more than one request per connection). Set to "Off" to deactivate.

KeepAlive Off

**KeepAliveTimeout**: Number of seconds to wait for the next request from the same client on the same connection.

KeepAliveTimeout 15

**Listen**: Allows you to bind Apache to specific IP addresses and/or ports, in addition to the default.

#Listen 12.34.56.78:80
Listen 80

**Dynamic Shared Object (DSO) Support**: To be able to use the functionality of a module which was built as a DSO you have to place corresponding `LoadModule' lines at this location so the directives contained in it are actually available _before_ they are used. Statically compiled modules (those listed by `httpd -l') do not need to be loaded here.

#Example:
LoadModule foo_module modules/mod_foo.so

**User/Group**: The name (or #number) of the user/group to run httpd as.

User apache
Group apache

**Section 2: 'Main' server configuration**

The directives in this section set up the values used by the 'main' server, which responds to any requests that aren't handled by a <VirtualHost> definition.
All of these directives may appear inside <VirtualHost> containers, in which case these default settings will be overridden for the virtual host being defined.
  
**ServerAdmin**: Your address, where problems with the server should be e-mailed.

**ServerName**: ServerName gives the name and port that the server uses to identify itself. If your host doesn't have a registered DNS name, enter its IP address here.

ServerName www.yourdomain.com:80
  
**DocumentRoot**: The directory out of which you will serve your documents.

DocumentRoot "/var/www/html"
  
**UserDir**: The name of the directory that is appended onto a user's home directory if a ~user request is received. To enable requests to /~user/ to serve the user's public_html directory, remove the "UserDir disabled" line above, and uncomment the following line instead

**DirectoryIndex**: sets the file that Apache will serve if a directory is requested.

DirectoryIndex index.html index.html.var
  
**AddIcon**: directives tell the server which icon to show for different files or filename extensions.

**AddType**: allows you to add to or override the MIME configuration file mime.types for specific file types.

**AddHandler**: allows you to map certain file extensions to "handlers": actions unrelated to filetype.

etc....  

**Section 3: Virtual Hosts**  
  
 If you want to maintain multiple domains/hostnames on your machine you can setup VirtualHost containers for them. Most configurations use only name-based virtual hosts so the server doesn't need to worry about IP addresses.

Refer the documentation at URL: http://httpd.apache.org/docs/2.2/vhosts/
  
> NOTE: NameVirtualHost cannot be used without a port specifier (e.g. :80) if mod_ssl is being used, due to the nature of the SSL protocol.  
{.is-warning}

 
**VirtualHost example**:  
  
Almost any Apache directive may go into a VirtualHost container. The first VirtualHost section is used for requests without a known server name.
  
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

**Tweaking Apache**
  
There are a number of little things that can be done to tune Apache performance and to lessen its impact on system resources. One of these things is tweaking the memory usage

Use  ps command to find memory usage of httpd, use command
  
```
ps -U apache -u apache u
```  
  
**Prefork Settings**  
  
Change the prefork settings according to your server needs

Example prefork directive
  
```
 <IfModule prefork.c>
StartServers 8
MinSpareServers 5
MaxSpareServers 20
ServerLimit 128
MaxClients 128
MaxRequestsPerChild 4000
</IfModule>
```

**KeepAlive**
  
By default, KeepAlive is turned off. By turning it on (KeepAlive On), we allow a single TCP connection to make multiple requests without dropping the connection. If KeepAlive is off, each element request will result in a new TCP connection and its associated overhead.
  
```
KeepAlive On

# MaxKeepAliveRequests: The maximum number of requests to allow
# during a persistent connection. Set to 0 to allow an unlimited amount.
# We recommend you leave this number high, for maximum performance.

MaxKeepAliveRequests 100

# KeepAliveTimeout: Number of seconds to wait for the next request from the
# same client on the same connection.
#
KeepAliveTimeout 2  
```  
  
