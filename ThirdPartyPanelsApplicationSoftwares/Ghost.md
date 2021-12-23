---
title: Ghost
description: 
published: true
date: 2021-12-23T15:55:18.577Z
tags: 
editor: markdown
dateCreated: 2021-12-23T15:55:18.577Z
---

# Ghost


> Note: This tutorial is based on CentOS 7
> 
{.is-info}

Ghost need Node.js version >= 0.10.x. First thing is to  install node.js

Enable EPEL REPO. Then run the following commands

```
yum update
yum -y groupinstall 'Development Tools'
yum -y install npm
```

**Install Ghost**


Grab the latest version of Ghost from Ghost.org:

```
curl -L https://ghost.org/zip/ghost-latest.zip -o ghost.zip
```

Unzip Ghost into the folder /var/www/blog (recommended install location):

```
unzip -uo ghost.zip -d /var/www/blog
rm -rf ghost.zip
```

Move to the new ghost directory, and install Ghost (production dependencies only):


```
cd /var/www/blog && npm install --production
```

When this completes, Ghost is installed!

Ghost defualt port is  2368.  So enable it in the firewall

```
iptables -A INPUT -p tcp --dport 2368 -j ACCEPT
```

Now  Start Ghost

```
cd /var/www/blog && npm start --production  >/dev/null 2>error.txt &
```

**Apache Ghost Configuration**


Now add apache ghost virtual host and Proxy Port 80 to 2368 For Ghost With Apache, so that we can load ghost website and admin portal without using port 2368

Create a  ghost.conf  /etc/httpd/conf.d   and the following to ghost.conf

```
NameVirtualHost *:80 
 <VirtualHost *:80> 
     ServerName websitename.com
     ServerAlias www.websitename.com
     ProxyRequests off 
     ProxyPass / http://127.0.0.1:2368/ 
     ProxyPassReverse / http:/127.0.0.1:2368/     
</VirtualHost>
```

If you want add it to already running website then add the following lines to the VirtualHost section of that perticulare website. As per the above example we installed ghost under /var/www/blog. So the document root directory of the website is /var/www. So add the following under that website's VirtualHost directory in apache configuarion file. 

```
ProxyRequests off
  <Location /blog/>
      ProxyPass  http://127.0.0.1:2368/blog/
      ProxyPassReverse  http://127.0.0.1:2368/blog/
  </Location>
```

Restart apache 

```
httpd -tD DUMP_VHOSTS
service httpd restart
```

DONE!.. You have successfully installed Ghost and configured it.

The ghost confguration directory is - /var/www/blog. All the configuration files are in there.  

The main configuration file is  - config.js

By default ghost use sqlite3 db. But it also support mysql and pgsql. 

Now Continue with Ghost Daemon 

