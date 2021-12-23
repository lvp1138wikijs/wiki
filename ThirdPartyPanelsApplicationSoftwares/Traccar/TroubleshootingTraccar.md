---
title: Troubleshooting - Traccar
description: 
published: true
date: 2021-12-23T18:11:46.846Z
tags: 
editor: markdown
dateCreated: 2021-12-23T18:11:46.846Z
---

# Troubleshooting - Traccar

We have 2 customer using GPS applications. 

**Traccar Website: https://gps.mypinhere.com**/
Server IP: 216.108.232.13
SSH Port: 5252
For this server, we installed and configured Traccar applications. The steps are here

**Error: 502 Bad gateway**

It happens when traccar process stuck/killed. Then the fix is to restart the applications

To restart applications. 

```
service traccar restart
service httpd restart
```

**Website: http://admin.mypinhere.com**/

Server IP: 216.108.238.115 

On this server, I have installed nginx, nodejs, MySQL and redis services. The customer has their own code team to configure the program. They are using nodejs scripts to run the applications through ngnix webserver.

**Nginx**
nginx -v
nginx version: nginx/1.15.0
Port: 80
Config files directory: /etc/nginx/

**Mysql**
Version: mysql Ver 14.14 Distrib 5.6.40
Mysql root user password: same as root user password

**Redis**
Version:v=3.2.10
redis config: /etc/redis.conf
#redis-cli ping
PONG

**NodeJs**
node --version
v8.11.3

 