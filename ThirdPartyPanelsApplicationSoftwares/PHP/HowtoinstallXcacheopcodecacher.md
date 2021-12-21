---
title: How to install Xcache opcode cacher
description: 
published: true
date: 2021-12-21T16:59:53.225Z
tags: 
editor: markdown
dateCreated: 2021-12-21T16:59:53.225Z
---

# How to install Xcache opcode cacher

serverXCache is a open-source opcode cacher, which means that it accelerates the performance of PHP on servers. It optimizes performance by removing the compilation time of PHP scripts by caching the compiled state of PHP scripts into the shm (RAM) and uses the compiled version straight from the RAM.

For installing Xcache opcode cacher please do the following steps.

1) Download xcache source code using the below commands.

```
cd /opt

wget http://xcache.lighttpd.net/pub/Releases/3.0.1/xcache-3.0.1.tar.gz
```
2)Untar tar ball using the commands:

```
tar -zxvf xcache-3.0.1.tar.gz

cd xcache-3.0.1
```

3) Compile and install xcahce using the below commands:

Use phpize command to prepare xcache as a PHP extension for compiling:

```
phpize
```
Configure, compile and install xcache:

```
./configure --enable-xcache
make
make install
```

4)Create xcache.ini file using vi editor in the directory /etc/php.d/.


```
cd /etc/php.d/

vi xcache.ini
```

Append configuration directives:

```
[xcache-common]
; change me - 64 bit php => /usr/lib64/php/modules/xcache.so
; 32 bit php => /usr/lib/php/modules/xcache.so
zend_extension = /usr/lib64/php/modules/xcache.so
[xcache.admin]
xcache.admin.auth = On
xcache.admin.user = "mOo"
; xcache.admin.pass = md5($your_password)
xcache.admin.pass = ""
[xcache]
xcache.shm_scheme =        "mmap"
xcache.size  =               32M
xcache.count =                 1
xcache.slots =                8K
xcache.ttl   =              3600
xcache.gc_interval =         300
; Same as aboves but for variable cache
; If you don't know for sure that you need this, you probably don't
xcache.var_size  =            0M
xcache.var_count =             1
xcache.var_slots =            8K
xcache.var_ttl   =             0
xcache.var_maxttl   =          0
xcache.var_gc_interval =     300
; N/A for /dev/zero
xcache.readonly_protection = Off
xcache.mmap_path =    "/dev/zero"
xcache.cacher =               On
xcache.stat   =               On
```

5) save and close the file.

6) Restart Apache webserver.

```
service httpd restart
```

7) Type the following command for xcache verification:

```
php -v

```

The output should be like:

```
PHP 5.1.6 (cli) (built: Nov 20 2007 11:11:52)
Copyright (c) 1997-2006 The PHP Group
Zend Engine v2.1.0, Copyright (c) 1998-2006 Zend Technologies
    with XCache 3.0.1, Copyright (c) 2005-2007, by mOo
```




