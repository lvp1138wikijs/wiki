---
title: Install Node JS with Apache in cPanel
description: 
published: true
date: 2021-12-27T16:49:40.903Z
tags: 
editor: markdown
dateCreated: 2021-12-27T16:49:40.903Z
---

# Install Node JS with Apache in cPanel

Install and configure Node JS with apache is quite simple procedure. Just follow the steps

**Installing Node JS**

SSH in as root to your server and download the latest node.js

```
wget http://nodejs.org/dist/node-latest.tar.gz
```

Extract it and rename it

```
tar -xvf node-latest.tar.gz
mv node-v7.0.0 node
```

Move into it and Install it

```
cd node
./configure
make
make install
```

Check the version on install

```
# node --version
v7.0.0
```

**Configure Node JS with Apache Website**

Open apache configuration fine using your favorite editor and go to virtualhost section of the website

> Replace Details
> 
> Replace the website name, username and locations with customer details.
{.is-info}


For example:

```
Assume the website is abcdxxx.com
Home location: /home/abcdxx/public_html - which contain normal php/html scripts
Node scripts want to run: /home/abcdxx/public_html/node
```

Open httpd.conf

```
vi /usr/local/apache/conf/httpd.conf
```

Go to the virtual host directory of abcdxxx.com and locate the following line

```
# To customize this VirtualHost use an include file at the following location
# Include "/usr/local/apache/conf/userdata/std/2/abcdxx/abcdxxx.com/*.conf"
```

Uncomment the Include line. Then the configuration look like

```
# To customize this VirtualHost use an include file at the following location
Include "/usr/local/apache/conf/userdata/std/2/abcdxx/abcdxxx.com/*.conf"
```

Save the configuration file

Now go to /usr/local/apache/conf/userdata/std/2/abcdxx/abcdxxx.com/ and create node.conf file with following entries

```
File: /usr/local/apache/conf/userdata/std/2/abcdxx/abcdxx.com/node.conf
```

**node.conf**

```
<Directory /home/abcdxx/public_html/node>
Options +Indexes +FollowSymLinks
AllowOverride None
Require all granted
</Directory>
ProxyRequests Off
ProxyPreserveHost On
ProxyVia Full
<Proxy *>
Require all granted
</Proxy>
<Location /node>
ProxyPass http://abcdxxx.com:8000
ProxyPassReverse http://abcdxxx.com:8000
</Location>
ErrorLog /home/abcdxx/public_html/node/error.log
# Possible values include: debug, info, notice, warn, error, crit,
# alert, emerg.
LogLevel warn
CustomLog /home/abcdxx/public_html/node/access.log combined
```

As per the configurations the node scripts will use port 8000

Now the following command to test the apache configuration file

```
/usr/local/apache/bin/httpd -tD DUMP_VHOSTS
```
Correct if any syntax error in the configuration file. If not restart the apache service. 

```
service httpd restart
```

Now go to /home/abcdxx/public_html/node and create the following following index.js file

**index.js**

```
var http = require('http');
var url = require('url');
http.createServer(function (req, res) {
console.log("Request: " + req.method + " to " + req.url);
res.writeHead(200, "OK");
res.write("<h1>Hello NODE :) </h1>Node.js is working fine on your server ! EnJOY");
res.end();
}).listen(8000);
console.log("Ready on port 8000");
```

Correct the ownership of node directory and it's files

```
chown -R  abcdxx:abcdxx /home/abcdxx/public_html/node
```

Testing Node JS through URL. Run the following commands

```
cd /home/abcdxx/public_html/node
node index.js &
```

'&' will help you run command in background. Now go ahead and load website through port 8000

```
http://abcdxxx.com:8000
```

It will show 

Hello NODE :)  
Node.js is working fine on your server ! EnJOY 


> May be port 8000 need to open in firewall. If website not connecting to port 8000 then try to open port in firewall 
> 
> iptables -I INPUT -p tcp -m tcp --dport 8000 -j ACCEPT
> service iptables save
> service iptables restart 
{.is-info}

