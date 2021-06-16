---
title: Apache Issues/HowTo
description: 
published: true
date: 2021-06-16T16:17:24.200Z
tags: 
editor: markdown
dateCreated: 2021-06-16T16:17:24.200Z
---

# How to change the Maximum apache connection

You can change it by modify apache configuration httpd.conf. Change the maximum client value. By default it is 256. 

Open httpd.conf using your favorite editor and modify MaxClients value

```
MaxClients       256
```
Then restart apache service using command /etc/init.d/httpd restart

## How to check Apache web server is active

Apache is running through default port 80. Check the port 80 is active or not.

- Login to server terminal as root via SSH
- Then run following command 

```
telnet localhost 80
 
if its up the result will be
 
# telnet localhost 80
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
```
If its not connecting, then restart apache.

## How to change the default umask for Apache/Php

Apache/Php umask determines the permissions for the newly created files. On a VPS / Dedicated server you can change the umask to suit your specific needs by editing:

```
/usr/local/apache/bin/envvars
```

There you should add:

```
umask 022
```

Right after that restart Apache and Apache/Php's default umask will become 22.




