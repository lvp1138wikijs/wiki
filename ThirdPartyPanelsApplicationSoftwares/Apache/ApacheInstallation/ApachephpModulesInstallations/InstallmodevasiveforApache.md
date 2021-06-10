---
title: Install mod_evasive for Apache
description: 
published: true
date: 2021-06-10T18:29:01.746Z
tags: 
editor: markdown
dateCreated: 2021-06-10T17:43:34.737Z
---

# Install mod_evasive for Apache


> mod_evasive is not a foolproof and complete DOS prevention system, but installing mod_evasive module for Apache will likely to reduce and stop certain DDOS attacks, minimizing the risks of web hosts and web sites been completely brought down inaccessible by malicious denial of service attack attempts.
{.is-info}


Here the steps for installing mod-evasive

1. Login to web server via SSH.
1. Continue with the following commands one by one for all version of Apache HTTPD server. wget command will download the current stable version 1.10.1 source tarball.

```
cd /usr/local/src
wget http://www.zdziarski.com/blog/wp-content/uploads/2010/02/mod_evasive_1.10.1.tar.gz
tar -zxvf mod_evasive_1.10.1.tar.gz
cd mod_evasive
```

3. For Apache 2.0.x , execute the following command:

```
/usr/sbin/apxs -cia mod_evasive20.c
 
Else, for Apache 1.3.x,
/usr/local/apache/bin/apxs -cia mod_evasive.c
```

**Above commands will compile mod_evasive to .so and subsequently add corrensponding AddModule and LoadModule lines into httpd.conf**.

4. mod_evasive comes with default configuration value preset, however, if webmasters want to configure and set the value themselves, the following parameters have to be added into httpd.conf Apache configuration file below the AddModule section.

- For Apache 2.0.x, add the following text to httpd.conf below AddModule section:

```
<IfModule mod_evasive20.c>
DOSHashTableSize 3097
DOSPageCount 5
DOSSiteCount 100
DOSPageInterval 1
DOSSiteInterval 1
DOSBlockingPeriod 600
</IfModule>
```

- For apache 1.3.x, add the following text to httpd.conf below AddModule section:

```
<IfModule mod_evasive.c>
DOSHashTableSize 3097
DOSPageCount 5
DOSSiteCount 100
DOSPageInterval 1
DOSSiteInterval 1
DOSBlockingPeriod 600
</IfModule>
```

**Save and exit the httpd.conf Apache configuration file**.

5. Restart the Apache server with the following command

```
/etc/init.d/httpd restart
```

